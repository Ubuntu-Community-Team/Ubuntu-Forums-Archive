---
title: "&quot;smart indent&quot; for a c++ IDE"
date: 2009-08-19
forum: Programming Talk
---

### Post by toofast.mv on 2009-08-19
Hey,
Recently made to switch to ubuntu, and i use geany for c++ code writing. One thing i can't seem to emulate, which is very useful is smart indent. Its in both matlab and ms visual studio C++ express (or whatever it is called). It basically lets you select the whole document, then auto indents it based off line breaks and curly brackets. Does anyone know any program for linux which offers this. Geany has "auto indent", which adds tab when you use { and }, but the feature is quite useless if you are try for example to add a for loop surround already existing code, because everything inside the for loop is incorrectly indented. 

Any help would be great, cheers.

---

### Post by Mirge on 2009-08-19
Eclipse CDT can auto-format existing code. You can customize the formatting as well.

---

### Post by jimi_hendrix on 2009-08-19
yes, it comes with many different styles for you to configure, FROM K&R to BSD

---

### Post by TheStatsMan on 2009-08-19
This is possibly not quite as good, but with Geany if you highlight the code you want indented, ctrl-i indents and ctrl-u unindents.

---

### Post by jpkotta on 2009-08-20
Emacs has the best indentation engine I've seen.  You can set just about every parameter and behavior and it has several predefined styles (I like BSD style with c-basic-offset = 4 and indent-tabs-mode = nil).  With extra effort you can do [smart tabs]("http://www.emacswiki.org/emacs/SmartTabs").  I have it set up so tab runs the indent command, so pressing tab indents the current line, where ever the cursor is.

Kate can do autoindent as well.  (I have never tried Eclipse).

---

### Post by toofast.mv on 2009-08-20
Hi,
I went with eclipse, because people have said its a good debugger. Thing is i can't seem to get it to auto indent my existing code. I have tried format, which does nothing. I have tried going into pref, and under c++, under code formatting, it has no formatting options. I have also gone c/c++ perspective. 

All i have installed is eclipse + eclipse CDT (and all dependancies). Any help would be great.
Thanks

---

### Post by Linteg on 2009-08-20
Select the code you want to auto indent and press Ctrl + I, or right click and select Source->Correct Indentation

---

### Post by toofast.mv on 2009-08-20
Ok i installed astyle, and that seems to do the job :) kr style seems to do the trick for me, since thats the style i already use when i write code normally. Cheers for the help. Though as you can tell by last reply, it is hard finding help on this subject, because people seem to confuse auto-indent (hit enter after { and it auto tabs) and smart indent, and most thing i googled offered help on the former.

---

### Post by jimi_hendrix on 2009-08-20
> **jpkotta said:**
> Emacs has the best indentation engine I've seen.  You can set just about every parameter and behavior and it has several predefined styles (I like BSD style with c-basic-offset = 4 and indent-tabs-mode = nil).  With extra effort you can do [smart tabs]("http://www.emacswiki.org/emacs/SmartTabs").  I have it set up so tab runs the indent command, so pressing tab indents the current line, where ever the cursor is.

Kate can do autoindent as well.  (I have never tried Eclipse).

for the record, vim has something similar

---

