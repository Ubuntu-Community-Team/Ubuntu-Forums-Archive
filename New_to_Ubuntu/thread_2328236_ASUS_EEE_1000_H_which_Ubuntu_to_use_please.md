---
title: "ASUS EEE 1000 H which Ubuntu to use please?"
date: 2016-06-19
forum: New to Ubuntu
---

### Post by benoit11 on 2016-06-19
Hello,

I have always used windows but would like to try and see if Ubuntu is faster than windows on an asus EEE 1000H which has only 1 gig of ram, could you please tell me which version of ubuntu shall I install? This is for a 32 bit processor.

Also, how will ubuntu find the drivers for each component of the motherboard?

Thank you,

Ben

---

### Post by Manuel_Olivier on 2016-06-19
Hello Ben

I've been using Ubuntu for 2 years now, and I must say this a better deal than Windows since I never had any difficulty to install/use apps in a small amount of time. Also I find this OS very quick (I use a lot of games and I run some programs), but that might also depend of you machine...
Moreover, if you have considerations for the limits of your RAM, know that you can use swap to enhance your performance (check out the Ubuntu documentation).

Ubuntu v. 16.04 has been released recently and so for it's working, either way I was on Ubuntu v. 14 LTS a few months ago and I was very satisfied. You can get tutorials to install ubuntu on your computer (one tip although: try to keep your Windows OS, even if you delete all the data stored in it. A dual boot is the best option so far, you never know what can happen if your computer ticks...)

So long

Manuel

---

### Post by sudodus on 2016-06-19
Welcome to the Ubuntu Forums :-)

I suggest that you start trying the newest version with long time support, ***16.04 LTS***. If there are problems I suggest that you try the previous (but still supported) version with long time support, ***14.04.1 LTS***.

I would suggest that you try a flavour of Ubuntu with a lighter desktop environment than standard Ubuntu (with Unity),

- ***Lubuntu*** with the ultra light LXDE
- ***Xubuntu*** with the medium light XFCE
- ***Ubuntu MATE*** with the medium light MATE

Many computers work with the Ubuntu flavours 'out of the box'. There are built-in drivers that work for most of the hardware, for example Intel graphics and wifi.
Some other hardware, for example nVidia graphics and Broadcom wifi, need proprietary drivers, that you can install 'afterwards'.

I'm not sure about your version of eeePC, but I have helped a friend of mine with an eeePC 900, and it works out of the box (without any proprietary drivers).

As mentioned by Manuel_Olivier, it might be a good idea to try ***dual booting*** (with an Ubuntu flavour alongside Windows). One reason to keep Windows is that you might have some peripheral device (printer, scanner ...) that works better with Windows because there is no [good] linux driver.

***Edit:*** Remember to ***backup*** your current system just in case, because installing an operating system is risky.

---

### Post by coldraven on 2016-06-19
I installed Xubuntu on a eeePC 900 and everything just worked, no hunting for drivers.As mentioned above for that spec. (1GB) a lightweight desktop is a better choice.
Get them all here:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by kurt18947 on 2016-06-19
I agree with Xubuntu/Lubuntu or variants. I'd also recommend looking at LXLE though I don't know when their 16.04 based release will be out. If you have some 4 GB+ flash drives, live USBs are a way to get a feel for the various 'flavors' without having to install. Remember that if you don't care for a certain app, it's trivial to remove it and install a preferred replacement. Some of my web sites didn't really care for Sea Monkey so I installed Firefox.

---

### Post by cblnchat on 2016-06-19
I would recommend Ubuntu MATE 16.04, simply because I've never been a fan of the other desktops.

Although I echo others' recommendations of dual-booting to make sure the system runs well and to keep Windows for anything that may work better in Windows.

---

### Post by Rex Bouwense on 2016-06-19
All the comments presented are excellent especially the one by sudodus concerning backing up your data.  That is very important because you never know what can happen and if you have data that you cannot live without you may have lost it forever or find yourself with a new problem of how to recover it.  I own an ASUS EeePC 1000H and have been running Lubuntu on it for years.  Currently it has 14.04 LTS on it and I am about to put the new LTS release on it.  It pretty much runs out of the box but if you are unsure, the dual boot option is always there.
Welcome to the forums and don't hesitate to ask if you run into a problem.  Remember, the only stupid question is the one not asked.

---

### Post by John Nagle on 2016-06-19
Xubuntu (44) runs well on  EeePC 1001px machines. I just installed on two of them. But Lubuntu installs stall at the point they first try to switch the screen to graphics mode.

---

### Post by kurt18947 on 2016-06-22
> **John Nagle said:**
> Xubuntu (44) runs well on  EeePC 1001px machines. I just installed on two of them. But Lubuntu installs stall at the point they first try to switch the screen to graphics mode.

When installing Lubuntu, have you tried the -nomodeset switch?

---

