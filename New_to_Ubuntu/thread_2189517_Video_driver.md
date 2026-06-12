---
title: "Video driver"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by celoitaliano on 2013-11-22
I want to install a video driver, but I have no clue how to do it.
I know my PC- Dell Inspiron 15 - intel core i5 has a Intel HD video card.
I went to their website and found this: 
**[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)**

but I have no clue what should I download.
I use ubuntu 13.1
Help me please!

---

### Post by papibe on 2013-11-22
Hi celoitaliano.

Intel video drivers are included on the default installation.

Let's confirm it. Could you open a terminal, run this command, and post the output?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by celoitaliano on 2013-11-22
Thank you for your attention! Here is the output:
"00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Dell Device [1028:0591]
    Kernel driver in use: i915"

The reason I suspected my video board is not installed is that when I run Steam, than Dota 2, a lot of errors happen.
Maybe I rushed my judgement a little bit, but I don't know other reason why the game would have so many mistakes.
The game presents collor malfunctions and takes too long to peform the easiest actions, sometimes crashes as well.

---

### Post by papibe on 2013-11-22
You have proper driver installed and in use.

You may try, at your own risk, to upgrade your driver to a new version which it hasn't been 100% tested, but it may solve some of the problems you are experiencing.

Open a terminal, and run these command, one per one.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
It may be necessary to restart your computer in order to the new driver to take effect. 

Let us know how it goes.
Regards.

---

### Post by celoitaliano on 2013-11-25
It fixed the problem, thank you!

---

