---
title: "No loading screen"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Spops on 2008-07-31
Hi guys,

I just installed 8.04.1 as a Wubi install on an older computer.  After I select the Ubuntu partition the screen just goes black for a good minute or so.  On my laptop I get a loading screen that says Ubuntu and a bar that goes back and forth.

Anyway to fix this on this older PC?


My System Specs are:


Intel Pentium 4 2.80 GHZ
512 MB of RAM

---

### Post by philinux on 2008-07-31
> **Spops said:**
> Hi guys,

I just installed 8.04.1 as a Wubi install on an older computer.  After I select the Ubuntu partition the screen just goes black for a good minute or so.  On my laptop I get a loading screen that says Ubuntu and a bar that goes back and forth.

Anyway to fix this on this older PC?


My System Specs are:


Intel Pentium 4 2.80 GHZ
512 MB of RAM

Ample spec for Ubuntu. You dont say if ubuntu finally loads properly to the desktop.

Also whats the graphics card?

If ubuntu loads you can use Accessories >Terminal and copy/paste this in

lspci | grep VGA

---

### Post by Spops on 2008-07-31
Oh, sorry yes it does finally load up.  I just do not get the screen that shows it is loading.  The graphics card is integrated.  Going to go and type that code in now i'll come back and tell you what it says.

---

### Post by Spops on 2008-07-31
It says Intel Corporation 82865G Integrated Graphics Controller

---

### Post by Spops on 2008-07-31
Anyone know how to fix this?

---

### Post by Spops on 2008-07-31
I'm sorry, but does anyone know why I am not getting the loading screen?  Or how I can fix it?

---

### Post by ET! on 2008-08-01
now thats a very old graphics chip.....try ctrl+alt+f1 and type the message you get

---

### Post by Spops on 2008-08-01
> **ET! said:**
> now thats a very old graphics chip.....try ctrl+alt+f1 and type the message you get

I created a thread in a different part of the forum to try and get some more help:

[http://ubuntuforums.org/showthread.php?t=876340](http://ubuntuforums.org/showthread.php?t=876340)

To answer your question it says (part of it is cut off on the screen):

Booting 'Ubuntu 8.04.1, kernel 2.6.24-9-generic'

Filesystem type is ntfs, partition type 0x7

[Linux-bzImage, setup =0x2a00,  size=0xd2598]

[Linux-initrd @ 0x1f6f9000,  0x7667f5 bytes}

loading,  please wait...

ubuntu 8.04.1 administrator-desktop tty1

administrator-desktop  login:

---

### Post by ET! on 2008-08-04
> **Spops said:**
> I created a thread in a different part of the forum to try and get some more help:

[http://ubuntuforums.org/showthread.php?t=876340](http://ubuntuforums.org/showthread.php?t=876340)

To answer your question it says (part of it is cut off on the screen):

Booting 'Ubuntu 8.04.1, kernel 2.6.24-9-generic'

Filesystem type is ntfs, partition type 0x7

[Linux-bzImage, setup =0x2a00,  size=0xd2598]

[Linux-initrd @ 0x1f6f9000,  0x7667f5 bytes}

loading,  please wait...

ubuntu 8.04.1 administrator-desktop tty1

administrator-desktop  login:

this means the kernel has booted perfectly....the problem is with your graphics chip...try typing gdm after logging in

---

