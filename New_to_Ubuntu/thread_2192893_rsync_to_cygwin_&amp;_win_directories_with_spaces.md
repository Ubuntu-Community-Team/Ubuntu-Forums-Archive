---
title: "rsync to cygwin &amp; win directories with spaces"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by JIdC on 2013-12-10
Hey everybody! 

I wanted to share with you something ackward.   I have been wrangling with rsync to sync files from  a win7 machine to one of my Ubuntu laptops. The problem is that the directories in win have spaces, and so the directories in Ubuntu. There is no problem to rsync from the top hierarchical level because I made sure that those directories high in the tree contained no spaces. Regrettably, as I built and built sub directories and sub sub directories, the no spaces mantra went into oblivion, and the result is that so far I had not been able to properly use rsync to just sync those directories with spaces.  Today I have found a solution and I want to share it with you.   Please note the inverted commas and the scape characters \ in my case-example below:

rsync -atnuvz [email]xx@192.xxx.x.xx[/email]:/cygdrive/d/juan/Padetepo/contabilidad_Padetepo_SL/'Facturas/ Padetepo /SL'/Listado/* /home/ji/j/Padetepo/contabilidad_Padetepo_SL/'Facturas Padetepo SL'/Listado 

Right, so the point here is that it also does work when the receiving end of the rsync command (my Ubuntu machine) is quoted as: /home/ji/j/Padetepo/contabilidad_Padetepo_SL/Facturas\ Padetepo\ SL/Listado   but IT DOES NOT WORK IF YOU USE BOTH THE INVERTED COMMAS AND THE BACKSLASH ESCAPE CHARACTER PLUS SPACE COMBINATION. Funny enough, in the Cygwin side it's the other way around, that is, it does not work if you actually use either just the inverted commas or the backslash escape character plus space combo. 

As said, it's been tricky for me and wanted to share it with you in case it helps other people.

---

