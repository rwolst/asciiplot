AP - Package that allows you to plot simple graphs in ASCII, a la matplotlib.
============================================================================

This package is a inspired from Imri Goldberg's ASCII-Plotter 1.0 (https://pypi.python.org/pypi/ASCII-Plotter/1.0)

At a time I was enoyed by security not giving me direct access to my computer, and thus to quickly make figures from python, I looked at how I could make quick and dirty ASCII figures. But if I were to develop something, I wanted something that can be used with just python and possible standard-ish packages (numpy, scipy).

So I came up with this package after many iterations based of ASCII-plotter.  I added the feature to show multiple curves on one plot with different markers.  And I also made the usage, close to matplotlib, such that there is a plot, hist, hist2d and imshow functions.


TODO:
-----
* [ ] imshow does not plot axis yet.
* [ ] make a correct documentation
* [x] publish on github


available markers
-----------------
	|marker  |  repr   | unicode     |     description                 | 
	|--------|---------|-------------|---------------------------------|
	|'-'     |         | u'None'     |  solid line style               |
	|','     |   ∙     | u'\u2219'   |  point marker                   |
	|'.'     |   ∘     | u'\u2218'   |  pixel marker                   |
	|'o'     |   ○     | u'\u25CB'   |  circle marker                  |
	|'of'    |   ●     | u'\u25CF'   |  circle marker                  |
	|'v'     |   ▽     | u'\u25BD'   |  triangle_down marker           |
	|'vf'    |   ▼     | u'\u25BC'   |  filler triangle_down marker    |
	|'^'     |   △     | u'\u25B3'   |  triangle_up marker             |
	|'^f'    |   ▲     | u'\u25B2'   |  filled triangle_up marker      |
	|'<'     |   ◁     | u'\u25C1'   |  triangle_left marker           |
	|'<f'    |   ◀     | u'\u25C0'   |  filled triangle_left marker    |
	|'>'     |   ▷     | u'\u25B7'   |  triangle_right marker          |
	|'>f'    |   ▶     | u'\u25B6'   |  filled triangle_right marker   |
	|'s'     |   ◽     | u'\u25FD'   |  square marker                  |
	|'sf'    |   ◼     | u'\u25FC'   |  square marker                  |
	|'*'     |   ☆     | u'\u2606'   |  star marker                    |
	|'*f'    |   ★     | u'\u2605'   |  star marker                    |
	|'+'     |   ✚     | u'\u271A'   |  plus marker                    |
	|'x'     |   ❌     | u'\u274C'   |  x marker                       |
	|'d'     |   ◇     | u'\u25C7'   |  diamond marker                 |
	|'df'    |   ◆     | u'\u25C6'   |  filled diamond marker          |


Examples
--------
* plot

```python
In [1]: from ap import ap
In [2]: import numpy as np
In [4]: x = np.arange(10)
In [5]: y = x ** 2
In [7]: print(ap.plot(x, y, marker='_s'))
  │                                               
  ┼+80.109                                     ◽  
  │                                               
  │                                               
  │                                               
  │                                       ◽       
  │                                               
  │                                               
  │                                  ◽            
  │                                               
  │                                               
  │                             ◽                 
  │                                               
  │                        ◽                      
  │                                               
  │                   ◽                           
  │              ◽                                
  ┼+1.701   ◽                                     
──┼────◽───────────────────────────────────────┼──
  │+0.046                              +8.97638   
```

* hist

```python

In [1]: from ap import ap
In [2]: import numpy as np
In [3]: x = np.random.normal(0, 1, 1000000)
In [4]: print(ap.hist(x, 20))
                        │                         
                       ∘┼+180303                  
                       |│ ∘                       
                       |│ |                       
                     ∘ |│ |                       
                     | |│ | ∘                     
                     | |│ | |                     
                     | |│ | |                     
                     | |│ | |                     
                  ∘  | |│ | |                     
                  |  | |│ | | ∘                   
                  |  | |│ | | |                   
                  |  | |│ | | |                   
                ∘ |  | |│ | | |                   
                | |  | |│ | | |  ∘                
                | |  | |│ | | |  |                
              ∘ | |  | |│ | | |  | ∘              
           ∘  | | |  | |┼+3828.47| |  ∘           
──┼--------------------------------------------┼──
   -4.39861             │              +4.48165   

In [5]: y = np.random.normal(0, 1, 1000000)
In [6]: print(ap.hist2d(x, y, bins=[20,20], width=30))
                              
                              
             ....             
           ..;;;;..           
         ..;-----;;.          
         .;-:!>>!:-;.         
        .;-!>???7>:-;.        
        .-:>?O$$O?>:;.        
       .;-!7OQHHQO7!-.        
       .;->?$HMNH$?!-..       
       .;->?$HNNH$?!-..       
       .;-!7OQHHQO7!-.        
        .;:>?O$$C?>:;.        
        .;-:>7??7>:-;.        
         .;-:!!!!:-;.         
          .;;----;;.          
           ...;;...           
              ..              
                              

```

* imshow

```python
In [1]: from ap import ap
In [2]: from scipy import misc
In [3]: im = misc.ascent()
In [4]: print(ap.imshow(im.T))
:::::::!!!!!!!!!!!!!!!:!: -....;.--::-;;;;>>>>>>>>
:::::!!!!!!!!!!!!!!!!!!:.          ::--;;-->>>>>7>
!!!::!!!!!!!!!!!!!!!!!!!;.---;;;;.;.::--;;-;>>>7>>
!:!!!!!!!!!!!!!!!!!!!!!!.----;:-:;:;::.--;;-->7777
!:!!!!!!!!!!!!!!!!!!!!!>----!;!.!;;;;>::--;;--7777
!!!!!!!!!!!!!!!!!!!!!!!!-;-.:;:;;-;:;>>::--;;;->77
!!!!!!!!!!!!!!!!!!!!!!!!..:;--;-;-;-.>>:::--;;-;77
!!!!!!!!!!!!!!!!!!!>:::;.;;-;-;;;;-;>>>>:::--;;;;7
-N!!!!!!!!!!!!!!-!!>>:!;.;;;.;--;.-.>>>>>:::---;;;
!QHO!!!!!!!!!!::>>!>!!!.. ........;>>>>>77:;:---;;
>HH!!CC!!!!!:!!:!!>!:;:...;;;;.....>>>>7777:;---;;
!H!7H>>CH>:!!!!:!>:-:::;  .;;.;;;;;>>>77777:::---;
>H!!!!H>N>>!!!!-!::-..;:;; ..;;;;.>>>>777777:::---
>CH!!>!OHC>>!::::;.....:;;.; .;.;.>>>77777777:::--
QHH7H$>QH7!>:!!;...;..;:-;.;;....;C>7777777777:::-
!!:HH>QHC>!>!;;..-.;;..--.-;;-;. ;!777777777777:--
!N!!>?HN$>>;..-;; ;.;;.-: -;;-;. ;;$77777777777::.
>QCON>!:H...;..-;;...;..::;-......;:777777777777::
>>!?Q!$HC....;.;-..-.-;;-Q ;>;;;; ;-Q777777777777:
>?Q>>!H7! ;....;-;; .;-.:C>>>>;;;.;-!7777777777777
HHHO>>!:!..; .;.;-....;>::$>>>;;;-.--H777777777777
>$!!:HH::..:. ;;;...>>>>>!Q>>>--;;..-!777777777777
$HQO;N7:- ..;....->>>>>>>;Q>>77--;-.-:H77777777777
7?>7:NH--. .;.;>>>>>>>>>>:!>777---;.-:>77777777777
.-Q>H>-:-. .:>>>>>>>>>>>>::N777----;;-:Q;7?7777777
;>;N!H>:;;.;>>>>>>>>>>>>77!Q7777---:.-::;.O7777777
7?;HO>::!!;->>>>>>>>>77777-Q7777----;-:-OM$-? ?777
Q..>7>--;-!!!>>>>>>>777777!:C777:---:;:7C7$;  >C??
;; >>---;!;-!!!!--77777777::H7777:---;->7O>:   !$7
;-!>>!-:.!;->!-!!!!77777777!Q7777-:---;>>? :     ;
-.!>77-:. ;-7!:-; ::::77777;Q7777:::-:;77>::    ..
:--777-:. ;-7!:  ;--:-:::77::Q7777:::-;77>!!::-;-N
::----;:..;--;:  ;:!7:>-;:::::::!Q!::-:?7>>>!!:QHH
.-:-!:;-;...-!:-..:;7:7-:7;.:$>:::::H>;?7:>>>!!O$7
; -:-!:-; .;-!:.;;-;;:>--7-;;Q-$?::::::>H:>>>>!!!O
;-;------.;;-!!;-:;-7;;-:7:?-:N!OO:>:::::::H$!!>!?
.;.;---::-;;-!!;;:OC:7?:-;-!::$:???>$::-::---:CH  
-;;..---:::;-:>?;:Q?:??:7-!--:$-C!--!-C-7;:-------
--; ;--.::::-:>??-!;:??7--??-;$:$$$:;-$-$.$-------
; .;.-;. .:::::7?-;Q7?!-?>?-::::7:??-7--:.-.-$----
 .;..--.   .:::::7>N7:-????>:---:?C?$-:7--.$ 7 :--
.; . -:    .-:::::::;--????:?-:--:$$::-!-;;: .OO-?
????C-- . ..??;:::::-?!C-C>7CC----!-;>$---:.. O-?O
CCCC>;- . ..C?C>:::::-CC-?-C7C-:;?C.C$:-O-O;; -.O-
CCCC-;-.....C?CCC>:::::-?--C-?--;--OO-->:----  ; 7
CCCC;--...;;>!>CC7;::::::-CC?:--;--O-->$-O;?;O -;O
CCCC--;. .;;?>CC?CC>O;-------O7-;;!-C;O:-O;$.--.O.
OOOO7-;. .;;O.7?-?OCOO.-------O--.- :O: O; -.-O;-!
OOOOQ-;. .;;O?:?C>C:>O!O;---------;$O!..O;O;O:>;:O
OOOOO-;. .;;C->7O?;?OOOOOO.------;->-;;O-;:--O-C -
```
