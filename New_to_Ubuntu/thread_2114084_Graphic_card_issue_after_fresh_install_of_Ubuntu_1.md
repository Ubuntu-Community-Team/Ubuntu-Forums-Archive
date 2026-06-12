---
title: "Graphic card issue after fresh install of Ubuntu 12.04 &amp; 12.10 64bits"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by whitefish10 on 2013-02-09
I am having a problem by which after I install Ubuntu 12.04  64bit it shows that my display breaks and shows nothing (turn off as of no signal). I tried Ubuntu  12.10 64bit and it worked, but after software update. The display breaks  also.


  My machine system requirment is :-


  Core i5 4GB RAM 1.5 TB Hardisk Graphics : ATI 6850
.
  My guess is that there is some sort of software incompatablity  between the gaphics card and the system. either the driver or the  kernal?


  Please advise me on how to fix it. And thanks.

---

### Post by Gone fishing on 2013-02-09
I would guess that the video card is running the monitor at an out of range resolution. Does the monitor come on if you run a tty terminal alt control F2 or run in recovery mode (select from grub screen (shift while booting))? If so have a look at  [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by whitefish10 on 2013-02-09
Nothing of that. It shows as of the graphics card is broken (I can  describe it as if it is light orange colour with some very small  squares). This only happens after I fresh install and update the system  (sudo apt-get update) then restart. 

So far. I have reinstalled Ubuntu 12.10 64 bit and didn't update the system, it just works well here.

I am checking if I can install the property drivers of my ATI card before doing the updates. It could resolve the problem.  

Please advise me.

Thanks,

---

### Post by Gone fishing on 2013-02-09
Yes you can install the proprietary drivers before updating. On a fresh install i usually install everything including the video drivers using the additional drivers utility and then do a full update.

---

### Post by whitefish10 on 2013-02-10
I did the installation of the ATI driver 13.1. But after the first reboot it had broken unity. I am trying to resolve it yet but I am not sure.

What I am thinking of is to CONTROL + ALT + 1. Then do a full update to the OS since I didnt do it "sudo apt-get upgrade" perhaps it will work after would.

I am sure what to do after this, I have already formatted my machine like 4 times just to resolve this but it is not working. Help me plz.

---

### Post by Gone fishing on 2013-02-11
I think this maybe the problem > Many users when they wished to upgrade their Ubuntu 12.04 up to 12.10, they encountered a problem concerning their graphics. This problem appeared only to AMD Radeon GPU users and especially to those who had Radeon HD 4000,  HD 3000 or HD 2000 graphics card.

[http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)

Hopefully the you can solve the problem by using the legacy drivers

---

### Post by verymadpip on 2013-02-11
A 12.10 install running a HD6850 with 13.1 drivers from AMD's website shouldn't need legacy drivers. 4xxx, 3xxx & 2xxx series cards (& older I expect) require legacy drivers.
Perhaps you need to install linux headers to get it to work correctly.  I know I had to.

You'd be looking for linux-headers-generic-[your kernel version here].

This may help:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by whitefish10 on 2013-02-11
I managed to resolve it by the following:-

1 - Since the issue is with Unity, I installed the gnome 3 after I did a fresh install of Ubuntu 12.10 64bit.
2 - In gnome 3 I installed the ATi drivers 13.1 and managed to work well after the restart.
3 - In gnome 3 after the restart it switch to the classic view since it was having issues with the drivers, I simply did a full update after that and gnome 3 was working again.
4 - From the login page I switch the view from gnome 3 to Unity and I am posting this message from it.

Thanks for your help.

---

