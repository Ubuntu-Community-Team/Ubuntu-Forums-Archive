---
title: "How to install Serious Sam - the second encounter in Ubuntu 6.10"
date: 2006-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by rev_b on 2006-11-07
Hi there. Very new to Linux, but Ubuntu is making me a step closer to ditching Windows.

I just want to share with you a workaround to install Serious Sam - TSE in Ubuntu 6.10. Aparently, SS installs and runs without troubles in most distros, but I was getting a "Syntax error: Bad substitution" in line 34 when trying to run the game. 

I used loki installer, [http://www.liflg.org/?catid=6&gameid=71](http://www.liflg.org/?catid=6&gameid=71) and after googling a bit I found a solution: after installing the game (it does it without problems) you have to edit the ssamtse script, and change the first line from 

*#!/bin/sh*

to 

*#!/bin/bash*

And there you go, you can run your SS game without too much trouble...:D

---

### Post by go_beep_yourself on 2007-11-24
Thanks for the tip. Have you got this game to work with gamepads? Also, did the game use only a square portion of the screen that was surrounded by black when you played?

---

### Post by go_beep_yourself on 2007-11-26
What can I do about this problem?

The cd is in the dvd drive, and the mount command shows that it is mounted. Why is it not being found and will not install?

[IMG]http://img160.imageshack.us/img160/3022/whatiswrongod1.jpg[/IMG]

---

### Post by rev_b on 2007-11-26
Hi there. You get a black border around the screen if you start with a resolution that is not suported by your X server configuration. Changing resolution in game options will fix it. I don't use gamepads, just keyboard and mouse. 

About the instalation I really can't help you, I haven't got that problem...

---

### Post by Andrej_BB on 2008-02-17
I have the same problem as well..
Unfortunately install program from Croteam has a checksum error, so now i cannot install the game.

---

