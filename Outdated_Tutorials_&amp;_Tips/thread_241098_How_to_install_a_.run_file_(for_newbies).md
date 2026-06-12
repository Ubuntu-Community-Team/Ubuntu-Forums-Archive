---
title: "How to install a .run file (for newbies)"
date: 2006-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by fatsheep on 2006-08-21
This is not a tutorial for the average ubuntu user.  Most users will already know everything I am about to say.  This is for the ubuntu newbie that downloaded a app in .run format and has no idea how to install it.  

**_How to Install a .run File:_**

For this How To I am going to be using the dummy name "example.run".   You should replace this with the name of the file you are trying to install.

**1.**  Open a terminal.  In Gnome the terminal is found in Applications>Accessories>Terminal.
**2.**  Navigate to the directory of the .run file.  For this example, I have mine on the desktop so I would  type in "cd ~/Desktop" and press enter.
**3.**  Type "chmod +x example.run" (press enter).
**4.**  Now type "./example.run", press enter, and the installer will run.

---

### Post by dafinga on 2007-04-01
thank you soooo much!

:guitar:

---

### Post by SniperKIng on 2007-04-02
yh thanks alot m8

---

### Post by steelxenon on 2007-04-03
An even more simplistic and user-friendly way of doing it; you can right click on the file, choose properties, go to the "Permissions" tab, check the "Allow executing file as program" check box. Close the properties, then double click the file, or right click and choose "Open" :shock:

---

### Post by zGhost on 2007-04-04
Wow thanks, is there a whole guide for this simple stuff somewhere? Ubuntu for dummies

---

### Post by Geekboy on 2007-04-06
Thanks a lot for this!  I downloaded the Linux installer for the Battlestar Galactica (Beyond the Red Line) game.  The commands worked perfectly.

BTW, the game is at [http://www.game-warden.com/bsg/](http://www.game-warden.com/bsg/).

---

### Post by Belathor on 2007-04-08
> /home/kyle/.setup26845: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


I'm getting the above error when I try to run this with the BtRL Demo. :(

EDIT: Installing ligtk1.2 through synaptic solved the problem.

---

### Post by r00tintheb0x on 2007-04-08
i believe "sudo aptitude install libgtk2.0-0" will do it.

---

### Post by r00tintheb0x on 2007-04-08
You may want to check this out also, [http://ubuntuforums.org/showthread.php?p=2403487#post2403487](http://ubuntuforums.org/showthread.php?p=2403487#post2403487)

---

### Post by Slipmyknot101 on 2007-04-09
Thank you. This guide was very informative. .run installed like a charm for me.

---

### Post by Linuturk on 2007-04-09
I was so lost with this .run file

I didn't realize I had to make it executable first. Silly me

---

