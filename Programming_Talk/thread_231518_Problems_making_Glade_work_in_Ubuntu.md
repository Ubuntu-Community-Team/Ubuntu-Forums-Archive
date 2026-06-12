---
title: "Problems making Glade work in Ubuntu"
date: 2006-08-07
forum: Programming Talk
---

### Post by theDentist on 2006-08-07
Has anyone any idea why I cannot compile my Glade programs.  I have just installed Glade on a fresh Ubuntu installation,  I also had to install the "make" program (thanks to this forums help), but when I test Glade, with a simple window, build the source code, then go the the terminal to complete the compiling to an executable, I fail at the configure and make stages.
when typing the command ./configure I get the following error message:

./configure: line 1250: syntax error near unexpected token `window,'
./configure: line 1250: `AM_INIT_AUTOMAKE(window, 0.1)'

remember I have typed no code as yet, just built the standard window.
Then when I type make I obviously get told there is no target or makefile.

Anyone help, as I can't even get started yet!!    :( 

Peter

---

### Post by ifokkema on 2006-08-08
Did you tell Glade to output C++ code? As far as I'm told, the C++ export functionality in Glade will be dropped soon, because it doesn't work anyway. I've tried to mess with it once, too, but couldn't get it to work either.

---

