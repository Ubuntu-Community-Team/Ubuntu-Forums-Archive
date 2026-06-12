---
title: "Ubuntu Won't start"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by kevbuntude on 2011-11-08
Hey I'm very new to Ubuntu and feel very over my head and would really appreciate some help. I'm running 11.10 on a macbook that is probably 5 years old. I have upgraded to a 250MB hardrive and two 1GB ram sticks.
I just removed compiz through my software center and my computer was pretty seized up (as it does a lot) so I restarted and when it rebooted, the regular Ubuntu wouldn't start, it only alows me to log in to recovery console and all I get is a terminal to work with which I don't know how to use. I am also given the option of Ubuntu 2d or a user defined Session.
I'm using another computer to type this. Please help.

---

### Post by kevbuntude on 2011-11-08
So I logged into 2d mode and I can get around at least.  In fact, its not too bad so far.

---

### Post by Quackers on 2011-11-08
DId you try re-installing compiz?

---

### Post by lolpenguin on 2011-11-08
Unity is a plugin for compiz, so by uninstalling compiz, Unity breaks. Unity 2D is a Qt application so it is not affected. Try reinstalling anything that was uninstalled.

---

### Post by kevbuntude on 2011-11-08
Ok I reinstalled compiz and restarted a couple times and its the same.  According to my history that's all that's been uninstalled in the last few weeks.  Any other ideas?

---

### Post by Quackers on 2011-11-08
As lolpenguin says you will need to re-enable the unity plugin in the CompizConfig Settings Manager. Unity should then be back - hopefully :-)

---

### Post by kevbuntude on 2011-11-08
> **Quackers said:**
> As lolpenguin says you will need to re-enable the unity plugin in the CompizConfig Settings Manager. Unity should then be back - hopefully :-)
Sorry, I'm foggy on some of the lingo.  I tried checking all of the boxes in the Unity section of my compizconfig manager and still no change.

---

### Post by eodrobot on 2011-11-08
Hi

I downloaded 11.10 and got a release which could not be trialled from CD - just went straight to install. Bah!

I downloaded another and tried to put it on a USB as well as a CD

The CD hung on the syslinux Peter Anvin black screen

The USB just did nothing.

I have Linux Mint 11 -LM Helena 8 and Win XP on a triple boot IBM laptop. This laptop is so forgiving, it will try anything.

I have, on my PC, a variety of distros in Virtual Box - my favourite being PCLinuxOS - my least Ubuntu 9.10 (the start of the rot, I loved 9.04)

I avoided 11.04 after the pain of installing it in Virtual Box - slower than any Windows install ever - no 3D even with guest additions-  after reading the outcry and hullabaloo about Unity.

I have two new coasters because I ran out of CDRW and used CDR

Don't think I will ever bother with Ubuntu again - until I have a new dual core 64 bit mega ram touch screen machine which it seems is the way Canonical is turning its back on even 2 year old PCs. Viva LinuxMint!

---

### Post by waynefoutz on 2011-11-08
Unity 2d might be all that machine can handle. Unity 2d isn't that bad, if you like Unity.

---

### Post by lolpenguin on 2011-11-10
Try running this:
```
unity --reset
```
then restart the computer and log in to the Unity session.

---

### Post by grahammechanical on 2011-11-10
One more thing.

At login the default desktop is the last used desktop. So, you login to Ubuntu 2D. You set up the Unity plugin but the next time you login it will still be 2D unless you selected Ubuntu at the login screen. I am assuming that you are using 11.10. It helps to know this. At the login screen or Greeter click the cog icon and select Ubuntu.

You may already know this. We do not know that you know it. We need to check. Some things do not take effect until after a reboot.

Regards.

---

