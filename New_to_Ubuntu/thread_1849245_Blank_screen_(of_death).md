---
title: "Blank screen (of death)"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by WillOTP on 2011-09-24
In efforts to install a Linux distro - namely Linux Mint, I was met with disappointment as each attempted install left me with a blank screen upon loading. No mouse, just a blank screen. This same problem happened with Ubuntu and a Wubi installation of Ubuntu. While no problems occur with my W7 installation, this problem is across the board. However, if I directly shut down the computer, my screen flashes, and for a split second I can see everything.

Wubi was installed successfully, but no visual GUI is able to be seen for a log-in unless I manually shut down my computer.

I expect this is a simple fix, but it's been a long time since I've played my hand at any Linux intro. Tips?

---

### Post by dearingj on 2011-09-24
When you see this blank screen, are you able to get to a textual login screen by pressing Ctrl+Alt+F1?

---

### Post by Rubi1200 on 2011-09-24
Hi and welcome to the forums WillOTP :-)

Please post the full specifications for the computer especially RAM and graphics card.

---

### Post by WillOTP on 2011-09-24
Specifications:

Dual Core T6600 Intel Processor
Intel GM45 Express Chipset (Graphics Card)
1066Mhz 4GB RAM
500GB Hitachi HDD

Anything else? :)

---

### Post by bcbc on 2011-09-24
Seems like there is a problem with the linux switching on the backlight with your intel card:
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/759104](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/759104) 

(Look closely at the screen - it's probably on, just the backlight is off).


You could try this ppa - I'm not sure it fixes it but it sounds like it should (I've used this ppa on a dell to fix the brightness controls): [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

Or you could try 10.04 - may not have this issue. Finally, if you wait a month, Oneiric 11.10 will be out and will likely have this issue solved (hopefully).

---

