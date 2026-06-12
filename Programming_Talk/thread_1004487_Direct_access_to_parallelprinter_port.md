---
title: "Direct access to parallel/printer port"
date: 2008-12-07
forum: Programming Talk
---

### Post by ged5 on 2008-12-07
I learnt commodore basic ,6502 assembler and m/c code back in the seventies, and have a program which I use every week to launch clay targets at a shoot I run. I made an interface box which connects to the printer port and 8 traps. It is currently in qbasic and won't run on anything newer than w98. I'm new to ubuntu, and wondered what would be the easiest language to learn to port it into that allows access to the parallel port, I just write the relevant value to the port, wait half a second then write 0 to the port. 
PS , I never learnt any of the  {{{ squiggle}}} languages :)

Thanks
Ged

---

### Post by iponeverything on 2008-12-07
I am partial to perl:

[http://www.geekinventions.com/?q=node/6](http://www.geekinventions.com/?q=node/6)

---

### Post by Delever on 2008-12-07
You may try it with python, using [portio]("http://portio.inrim.it/") library. There is also pyParallel module.

I have no needs for it myself, this is what google search told.

---

### Post by ged5 on 2008-12-07
Thanks for the replies.
I had wondered about perl and python because they seem to be considered as good starting languages. Now I know they are both capable of doing what I need I can try to teach my old brain some new tricks.:D

---

