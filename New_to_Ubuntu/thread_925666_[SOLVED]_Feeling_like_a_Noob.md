---
title: "[SOLVED] Feeling like a Noob"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by janes604 on 2008-09-20
Hi, So i'm felling like a bit of a noob here 
i'm so new to Ubuntu i'm notconfused: sure how to install this file :confused: 

****.tgz

 how would i go about doing this ? i have been searching and i can't seem to find a answer that works 

Terminal commands would be great

---

### Post by Iowan on 2008-09-20
Check **man tar**.  Your file  is zipped, so read about the -z option.

---

### Post by mc4100 on 2008-09-20
a .tar.gz will more often than not contain a programs source-code, which you will have to compile (= not easy for a noob), but if you do still want to do, we're here to help, and can show you where to start.
It's far easier to list what stuff you want to do with some software, and we can recommend a good application that can be click-installed through:
Applications -> Add/Remove
This is the easier, and most secure, way; as you are running supported programs that will be updated when you upgrade Ubuntu.

---

### Post by janes604 on 2008-09-20
i am looking for a Play Staion 1 or 2 emulator for linux ..lol 

any suggestions?

---

### Post by kansasnoob on 2008-09-20
Exactly what are you trying to install?

Oops, overlapped. I'm clueless about gaming.

---

### Post by Iowan on 2008-09-20
> **mc4100 said:**
> It's far easier to list what stuff you want to do with some software, and we can recommend a good application that can be click-installed through:
Applications -> Add/Remove
Good point - most of what you want *may* be available in repositories.  You can use Synaptic or Aptitude (or ask here) to learn what/where.

---

### Post by mc4100 on 2008-09-20
Not much experience, but you could try PCSX:
Simplist way is:
Open a terminal (through Applications -> Accessories)
And right-click copy/paste:
```
sudo apt-get install pcsx-bin
```
And then put in you're password (no ***'s feedback like when logging in)

---

### Post by janes604 on 2008-09-20
the file is called 

pcsx2.i386.tgz it is a playstation emulator

how can i make this work ??

---

### Post by janes604 on 2008-09-20
> **mc4100 said:**
> Not much experience, but you could try PCSX:
Simplist way is:
Open a terminal (through Applications -> Accessories)
And right-click copy/paste:
```
sudo apt-get install pcsx-bin
```
And then put in you're password (no ***'s feedback like when logging in)

Ok  sow that seems to have worked but now i can't locate  the installed program

---

### Post by mc4100 on 2008-09-20
> **janes604 said:**
> Ok  sow that seems to have worked but i can't locate the program now to run it ....

Ok, well, we can make a launcher in the menu later on, but lets just check it's working. Press Alt+F2 to bring up the run applications dialog; and type "pcsx", and if that doesn't work "pcsx-bin".

---

### Post by janes604 on 2008-09-20
Thanks that worked!

now how do i make the launcher?

---

### Post by steveneddy on 2008-09-20
> **janes604 said:**
> the file is called 

pcsx2.i386.tgz it is a playstation emulator

how can i make this work ??

Put the file on your Desktop.

Right click and select Extract.

Go to the Read Me folder and read it.

Navigate to the folder on your desktop within Terminal.

It will be a series of commands like.

./configure
make
sudo make install
sudo make clean

---

### Post by mc4100 on 2008-09-20
> **janes604 said:**
> Thanks that worked!

now how do i make the launcher?
To make the lancher, again, type Alt+F2 and this time type:
```
alacarte
```
Which is the menu editor; 
[list][*]Choose the "Games" folder on the left-hand pane. 
[*]Then click somewhere in the right-hand pane. 
[*]Click "New Item".
[*]Name it what you like
[*]For the command, type what you type earlier in the "Run Application" window.
[*]If you like, add a comment.
[*]Click OK
[/list]
... done.

---

### Post by janes604 on 2008-09-20
Thanks again 
you sure made that simple !
ubuntu FTW!

---

