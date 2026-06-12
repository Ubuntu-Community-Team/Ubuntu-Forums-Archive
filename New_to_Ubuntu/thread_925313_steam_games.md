---
title: "steam games"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-20
okay, as you all know I am new to linux although loving every minute of it
(including the penguin invasion of my desktop) but now, I have something that might require wine, wich I have no clue on how to use. my question is this, on a windows comp i have tf2 installed and running, but i dont feel like switching my graphics card back and forth every time i want to play tf2
I read somewhere that games run faster on wine in linux on windows
(i have no clue how valid this statement is, just stumbleupon it) but my overall question is this:


How can I run steam games on linux?

---

### Post by oneadvent on 2008-09-20
I use CS and DOD from steam, and you can just go to their website and download the .msi file and install it like normal.

First you will need to install wine tho:

```
sudo apt-get install wine
```

some people like playonlinux, but I disagree, wine really works well enough.

Steam works well too.

---

### Post by hyperhopper on 2008-09-20
what is a msi file and how do i install it?

---

### Post by oneadvent on 2008-09-20
dont forget to download sudo apt-get install wine first, then goto [http://store.steampowered.com/](http://store.steampowered.com/) and it is on the left side, a green button, just put it on your desktop and double click it like a normal windoze program and it will bring up the installer.

Its pretty simple, just dont over think it.

and an msi file is an installer from windoze, its their attempt to throw off wine I think because it used to not support it at all. :)

---

### Post by hyperhopper on 2008-09-20
why would theyy want to throw off wine?

---

### Post by oneadvent on 2008-09-20
I was kidding actually, I was referring to the fact that for the longest time wine did not support msi files. I was pleasantly surprised one day when it suddenly worked w/o an issue. I mean what is the point of having an msi instead of an exe to install the program? 

Did the program install like it should for you?

---

### Post by hyperhopper on 2008-09-20
wine is installed, and installing TF2, lol now i have 1 gb of hard drive space left after tf2 is done, gonna open a thread to figure out how to take the hard drive in my hand and "mount" or whatever linux does to get it to try to get some more memory.

---

### Post by oneadvent on 2008-09-20
you should be very careful and not fill up the hd, i have crashed my system many times that way. i use the 33 percent available rule: always leave 33 percent available.

Good luck

---

### Post by hyperhopper on 2008-09-20
uh oh-- better get that second one in quick!

---

### Post by hyperhopper on 2008-09-20
NOOOOOOOOOOOOOOOOOO


now when i run tf2 i get a full black screen, and when i move my mouse around i hear little *tck* *tck*'s

HOW CAN I GET IT TO WORK?

---

### Post by B00R4dL3y on 2008-09-20
Under the "My games" tab:

right-click "Team Fortress 2", select "Properties"

click "Set launch options..."

add "-dxlevel 81"

should work after that.  I have "-dxlevel 81 -window" to get mine to play in a window.

TF2 works okay, but I'd rather just reboot and play it under windows if I know I'll be spending more time playing.

---

### Post by hyperhopper on 2008-09-20
the comp im on deosnt have A windows or B enough space to put windows on it

---

### Post by hyperhopper on 2008-09-20
okay, i did that,  but i still get the same result with 3 exeptions

A i see a dude witha a valve on his head before startup, along with the name of the developer

B during the black screen with the *tck* noises i see a ligher batch of grey where the valve head was, although it is not much brighter that the rest

C i get to listen to cool spy action music at the black screen 


PLEASE HELP ME

---

### Post by hyperhopper on 2008-09-20
can anybody help me heree

is there hope or should i just uninstall

btw, does no tf2 mean no portal?

---

### Post by hyperhopper on 2008-09-20
ok i give up, somebody tellme how to get tf2, steam, and wine COMPLETELY off my system!!!

---

### Post by oneadvent on 2008-09-20
you could try opening a new thread in the gaming section.

And you should try googling your problem, but after those things do not work,

```
sudo apt-get remove wine
``` will.

Good luck with your issues.

---

### Post by hyperhopper on 2008-09-20
will removing wine kill the steam and tf2 files?

---

### Post by oneadvent on 2008-09-20
It should get rid of wine and all programs installed under it, if it does not, wine's folder is .wine under your home partition and after you uninstall wine, you can safely remove that folder. That is where all files are written to when installing programs under wine.

---

### Post by hyperhopper on 2008-09-20
thank you.. well ill just wait untill i get another computer to try again.

awww well 

thx anyways...

---

