---
title: "WoW installation"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by BossGreen on 2008-07-12
I got the wow discs and i have wine installed on my computer.
when i look at the files on the cd, i says they are executable.  but when i click them, it doesnt execute them,  it doesnt do anything at all actually.
when i right click it and choose open with wine windows program loader, nothing happens as well.
how do i make it install the stuff from the cd basically using wine.

---

### Post by Nexusx6 on 2008-07-13
Hola,

Try these directions found at the Wine AppDB for WoW:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

---

### Post by BossGreen on 2008-07-13
none of them are for xubuntu tho...
does it even matter?

---

### Post by Nexusx6 on 2008-07-13
No, it shouldn't to be honest. Wine is rather 'stand alone', so you should be just fine :)

---

### Post by BossGreen on 2008-07-13
that site doesnt really give instructions on how to install it, it just tells how to fix bugs (book marked the page for future reference :))
are there any sites that say how to install it using wine?

---

### Post by Nexusx6 on 2008-07-13
you could try a google search for Wow in Wine, but lets try this first~

You said that double clicking had no effect. This is odd, Wine *should* associate itself with all .exe but lets give it a shot from the terminal.

Open up Terminal and navigate to your CD-ROM drive, it should be something like /cdrom/ or /media/cdrom0. With a little poking around, should find it no problem. So for example, you'd want to type something like this in Terminal:
```
cd /media/cdrom0
```

Once you have 'cd' into the disk drive, you're going to want to invoke the wine command on the .exe you want to run. That is to say, if you want to run "setup.exe" from the disk, type this:
```
wine setup.exe
```
This should get the ball rolling for you. If there is an "autorun.exe" file, you could try wine *autorun.exe first. * Wine has a very high gold raiting in the Wine AppDB, so hopefully this start should get everything going smoothly.

---

### Post by hyper_ch on 2008-07-13
[https://wiki.ubuntu.com](https://wiki.ubuntu.com) --> search there for "wow" or "warcraft" and you get an easy to follow guide...

---

