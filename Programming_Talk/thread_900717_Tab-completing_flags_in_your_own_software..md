---
title: "Tab-completing flags in your own software."
date: 2008-08-25
forum: Programming Talk
---

### Post by victor.zamanian on 2008-08-25
Hello lads and (hopefully) ladies.

You know how when you type in "cat" or "ls" or "aptitude" or "mplayer" or... well, pretty much any program in the terminal, followed by a "-" and then hit TAB twice, a list comes up with the available flags for that piece of software? 

Well, my question is: How would I go about coding up my own program (in C for instance) for which that function of bash would work? Note here that I don't need a lesson in C, just what code I need to include or otherwise do in order to enable this for my program. But obviously, tell me anything you feel I need to know in order to pull it off.

Say for instance I wrote a piece of software that tells me the temperature outside my window, but it needs a flag that determines which scale to print the value in:

I type in:
```
~$ ./tellMeTheTemperature -
```
and then hit the tab key 2 times, and the following is printed:
```
~$ ./tellMeTheTemperature -
-fahr -cels -kelv
~$ ./tellMeTheTemperature -
```
I then hit **c** to show the temperature in Celsius and hit tab again to auto-/tab-complete it:
```
~$ ./tellMeTheTemperature -**c**els
The temperature outside is... just stick your head out the window
and check for yourself you lazy nerd °C.
~$
```
Thanks for any help!

P.S.
I never did poke my head out but it looks about... 10-ish or so, °C. ._.

---

### Post by mssever on 2008-08-25
Drop a file in /etc/bash_completion.d. See other files in that dir for info. See also /etc/bash_completion.

---

### Post by dtmilano on 2008-08-25
It's not your program, it's bash (bash-completion) who provides the options.
Take /etc/bash_completion.d/debconf as an example and write your own.

---

### Post by victor.zamanian on 2008-08-26
Ahhh, so that's how it works. I'll look into that. Thanks so much guys, all the best!

---

### Post by victor.zamanian on 2008-08-27
One more question though:

How do configure scripts make this happen? Is this also a feature of bash that it looks within the configure script to see the available options?

---

