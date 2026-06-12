---
title: "problem with graphics tablet trust 15356"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by Journeyman1962 on 2011-10-11
Hi everyone,

Hoping for some help with a graphics tablet.
It's a Trust 15356.
Lucid won't recognise it.
Have trawled the forums and followed all the tips so far - including adding wizardpen (drmo) repository. updating repos and downloading drivers - libs etc..
I tried this in the summer and it worked fine. Since then, the computer has been cleaned and a new install of windows xp and Lucid put on it. It's a dual boot. Windows has no problem with the graphics tablet.

Any suggestions gratefully reveived. Thanks.

Tim

---

### Post by Favux on 2011-10-11
Hi Tim,

Let's find out who makes the tablet.  Post the tablet line in the output of:
```
lsusb
```
in a terminal.

---

### Post by Journeyman1962 on 2011-10-11
Thanks. I'm investigating this for a friend. Computer is not here. I'll get the info and/or put him onto the thread.

Tim

---

### Post by aupadenis on 2011-10-11
hi, i'm the one who's got the problem. the manufacturer? trust tb-5300. tablet line in the output? sorry, dont know what you mean. all i wanna do is get my tablet installed. i've done what i've read on different googled pages, tried different things in different programs, synaptic this, soemthing else the other beginning with sudo and other stuff i dont understand. i'm not into this unbuntu stuff to get geeky, i just want my stuff to work, if its too difficult i'll stick to windows. i've got no axe to grind, no windows/bill gates loyalties or anything, just wanna know if my stuff can work or not, if not i'm out of here.
my tablets already been installed once - not by me -but had to reinstal both windows xp -vienna- & ubuntu 10.4, now the tablet is invisible & i have to use a mouse. if i leave the stylus lying on on the tablet itslef it interferes with the mouse, so something must be getting picked up somewhere
sorry if i'm sounding brusque & prickly & unfriendly, but.... x x :-)

---

### Post by Favux on 2011-10-11
Hi aupadenis,

Welcome to Ubuntu forums!

Don't worry, linux just has a slightly different way of doing things than Windows.  It's not hard and I'll walk you through it.

In Applications > Accessories click on the Terminal.  When the terminal pops up enter the command:
```
lsusb
```
A bunch of output will appear.  Find the line with the tablet in it and copy and paste it into your next post.

---

### Post by aupadenis on 2011-10-11
hi, thanks for answerin, can't do what you asked me to do right mow, am in windows backing up documents etc, will take me at least 45 minutes to boot back into ubuntu, but then i'll have a go at doing what you said :p

---

### Post by aupadenis on 2011-10-11
here it is

denis@denis:~$ lsusb
Bus 002 Device 007: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
Bus 002 Device 006: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 003: ID 059b:0277 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Favux on 2011-10-11
Alright.  It is a UC-LOGIC tablet and that is suppose to use the WizardPen driver.  Did you install DoctorMO's PPA for it as Journeyman1962 said?
```
Bus 002 Device 007: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
```
Vendor ID = 5543 and Product ID = 0004

In your next post include the output of this command in the terminal:
```
xinput list
```

By the way here is the wiki with the WizardPen instructions:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

### Post by aupadenis on 2011-10-11
i don't know what to do with the bit of code you wrote, this means nothing to me, tried pasting it in the terminal, i guess thats not what im suppsosed to do

Bus 002 Device 007: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet

---

### Post by Favux on 2011-10-11
I was just showing you that the lsusb output told us a lot about the tablet.

The important question is did you install the driver PPA?  If not you'll need to install it.  The wiki tells you how to do that pretty much at the beginning.

---

### Post by aupadenis on 2011-10-11
by the way, even tho i still dont kno what the previous bit meant, when i put 

xinput list

into terminal i get this

denis@denis:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS2++ Logitech Wheel Mouse                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=11    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                     id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
l

---

### Post by Favux on 2011-10-11
OK, what xinput list shows us is the usb driver in the kernel sees the tablet:
```
&#9116; &#8627; UC-LOGIC Tablet WP5540U id=8 [slave pointer (2)]
```
And that also gives us the keyword(s) needed for a match, if we need one.

So either you don't have the WizardPen X driver installed or there is something wrong with the 70-wizardpen.conf located at /usr/lib/X11/xorg.conf.d so you don't get a match to the tablet.

Did you install the driver PPA?  Do you need help with that?  Also after you install it you have to reboot.

The .conf files set up or configure devices.  The X server is the X windowing system that draws the pictures on the screen.  So you need two drivers.  The kernel one that pulls in the usb data, which you have, and an X driver that talks to the X server so things actually get drawn on your screen.

---

### Post by aupadenis on 2011-10-11
yes, i did the ppa bit thru the sofware & edit & add options

---

### Post by Favux on 2011-10-11
Alright so you added the PPA through the Software Sources.

So let's check on the wizrdpen.conf.  As I said you should be able to navigate to it at /usr/lib/X11/xorg.conf.d in Places (Nautilus) and then view the file or open it in a the text editor from a terminal:
```
gedit /usr/lib/X11/xorg.conf.d
```
Basically we want to know if it is there and what the contents are.

---

### Post by aupadenis on 2011-10-11
sorry, have had to leave ubuntu & go back into windows to get some work done.
thanks for your time & patience , i can only reply to your last post the next time i go into ubuntu

---

### Post by Journeyman1962 on 2011-10-11
Favux

Thanks for your help.

Tim

---

