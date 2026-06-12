---
title: "[SOLVED] i can't get wine to work !"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Mallarmist on 2008-08-15
hi.
i have problem with wine 1.0.
i downloaded it, ran the configure thing, then a configure log thing came up.:confused:

what is next?

---

### Post by tahina on 2008-08-15
When you say, "downloaded it, ran the configure thing", do you mean you didn't use Add/Remove or synaptic to install it (or "sudo apt-get install wine" from command line)?

---

### Post by phidia on 2008-08-15
See if a .exe file will run by clicking on it or opening it in terminal.
If you get errors copy and paste them here.

---

### Post by LowSky on 2008-08-15
WINE is just a backend to get some (as in only a few) Windows rograms to work. what programs do you want to install?

---

### Post by Mallarmist on 2008-08-15
no, i didn't.

how do i do that ?

P.S i'm a complete noob.

---

### Post by LowSky on 2008-08-15
> **phidia said:**
> See if a .exe file will run by clicking on it or opening it in terminal.
If you get errors copy and paste them here.

in terminal type

```
[code]wine ***/path/to/the/program/.exe***
```

---

### Post by Mallarmist on 2008-08-15
i want steam to work, msn & a couple of other things.

---

### Post by LowSky on 2008-08-15
> **Mallarmist said:**
> no, i didn't.

how do i do that ?

P.S i'm a complete noob.

ok?

What didn't you do, is it installed? does it show up in your progrmas menu?

---

### Post by LowSky on 2008-08-15
> **Mallarmist said:**
> i want steam to work, msn & a couple of other things.

Wine will run [how to install steam]("http://ubuntuforums.org/showthread.php?t=540039")

[install MSN messenger]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=127")

What else?
Just so you know Ubuntu and Wine are not a replacement for Windows. Some stuff just wont work that need Windows.

---

### Post by ooobuntooo on 2008-08-15
> **Mallarmist said:**
> i want steam to work, msn & a couple of other things.

Steam will work, MSN won't (but there are plenty of alternatives, [emesene]("http://www.emesene.org/") being the best IMO.)

This might want moving to the "Wine" section.

---

### Post by Mallarmist on 2008-08-15
ok, now it's working. :D:D

i did the thing in the terminal.

thanky you all! :D

---

### Post by tahina on 2008-08-15
You can use pidgin (installed by default) for msn (and icq, gtalk etc...), but pidgin hasn't got video working with msn. Another program is aMSN, which does have video for msn aswell. 

As far as nudges and other msn stuff like that, I don't know if there's a program to do that. 

You can install both emesene and/or aMSN with "Add/Remove..." which you can find at the bottom of the "Applications" menu.

---

