---
title: "gedit - comment code"
date: 2014-12-05
forum: New to Ubuntu
---

### Post by flex567 on 2014-12-05
How can I comment or uncomment a block of code by highlighting and pressing a key ?

---

### Post by nerdtron on 2014-12-05
Block of code? I think only  lines can be commented? and it depends on what type of code it is.

---

### Post by coldcritter64 on 2014-12-05
> block of code by highlighting and pressing a key ?                  If I am reading your question right, then what nerdtron said sounds correct, only lines of code can be commented out (by inserting the cursor at each  line start and by pressing the "shift + 3" keyboard combination for a # symbol to be inserted at the start of each line).

_*Note: when text wrapping is in use in gedit long lines of code may take up several lines,*_  to see the actual start of each line needing a # symbol either turn off text wrapping and use the scrollbar that appears OR with text wrapping on use the line numbering  function of gedit so each new line starting point is clearly visible. 

Text wrap and line number preferences are in the Edit  menu > Preferences > View Tab. 

For a block of code each **individual new line** needs a # symbol placed at the start of the line to comment it out fully as a block. 

See the attached screenshot, I have gedit set to use text wrapping so I also turn on line numbering for easier visual indication of the line starting point for any commenting out of lines of code/text etc.

[s]Commenting out code is not a simple "highlight a block of code/text and press one button" action, not like using the code or quote tag buttons in the post editors here if that is the sort of usage you were thinking of.[/s] **Edit 2:** _*this struck out info is seriously wrong, see post 6 by CantankRus*_ for the correct details, highlight and press a 2 or 3 key combination, extremely easily done. Sorry for the misinformation OP.

Edit: @ OP note Impavidus' next post for symbols used with different code types for commenting out purposes.

---

### Post by Impavidus on 2014-12-05
It would depend on the type of code. Shell scripts use # before the commented line, TeX uses % in the same way, C++ uses //. Block comments would use /* .... */ in C or <!-- .... --> in xml. These can be several lines long.

---

### Post by flex567 on 2014-12-05
in emacs this command is c++->Comment out Region (C-c C-c)

---

### Post by CantankRus on 2014-12-05
In 14.04 I have a "Code Comment" plugin in gedit (3.10.4).
Highlight a block of code and press ctrl+m to comment and shift+ctrl+m to uncomment.
I only write basic shell scripts and it comments using the "**[COLOR="#FF0000"]#[/COLOR]**"  symbol.
I tested on a lua script and it inserts the correct "**[COLOR="#FF0000"]--[/COLOR]**" and
in xml it uses "**[COLOR="#FF0000"]<!--[/COLOR]**" and "**[COLOR="#FF0000"]-->[/COLOR]**" to comment code so I'm assuming it works with lots of different code.

Don't remember installing but it appears to be in the gedit-plugins package.
```
sudo apt-get install gedit-plugins
```

Enable the plugin in the preferences > plugin tab.

---

### Post by coldcritter64 on 2014-12-05
> **CantankRus said:**
> In 14.04 I have a "Code Comment" plugin in gedit (3.10.4).
Highlight a block of code and press ctrl+m to comment and shift+ctrl+m to uncomment....

Same here after checking ... looks like I got some words to eat back in post 3 ... Now edited out (with stikeout tags) and noted as wrong.

Thanks for pointing that out CantankRus, I had absolutely no idea the plugins pack was even installed here or that the code plugin existed. That will come in extremely handy now I know its there. Cheers.

---

