---
title: "Purple Screen of DEATH!"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by MyVitalRemains on 2012-08-15
I just finished installing Ubuntu and everything seemed to work all fine and well until I restarted after I finished the install. Every time I boot Ubuntu (not on recovery mode) I get a blank screen (although I do hear sound). The same thing happens when I boot Windows XP, it starts normally with me seeing the Windows XP loading thing, but afterwards I am just greeted with a blank screen with a few sounds. Does anyone know how I can solve this issue? :(

---

### Post by MyVitalRemains on 2012-08-15
My main problem with the WinXP boot is that I cannot get any output (except for sound). I know that it is working (WIndows XP, that is) fine except for this one issue. Although I cannot get Ubuntu running unless it is on recovery mode. Should I use boot repair?

---

### Post by oldfred on 2012-08-15
If both are not working I might check connections first.

But with Ubuntu video drivers are often an issue. What video card/chip do you have? Sometimes other options may be required.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by MyVitalRemains on 2012-08-17
> **oldfred said:**
> If both are not working I might check connections first.

But with Ubuntu video drivers are often an issue. What video card/chip do you have? Sometimes other options may be required.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
I have an Intel Atom with Intel integrated graphics.
:(

---

### Post by oldfred on 2012-08-17
I thought Intel worked out of the box normally. Not sure what version is with the Atom processor. Some use the generic setting as this is more the default on the liveCD. Did liveCD work ok?

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by MyVitalRemains on 2012-08-17
> **oldfred said:**
> I thought Intel worked out of the box normally. Not sure what version is with the Atom processor. Some use the generic setting as this is more the default on the liveCD. Did liveCD work ok?

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

The LiveCD works fine and such, and I can get Ubuntu and Windows XP to work (now at least), but my main problem is that in order to get output from the screen, I have to put it on standby and back on again. This happens on both XP and Ubuntu, although the [WinXP intro screen]("https://encrypted-tbn3.google.com/images?q=tbn:ANd9GcRjm7sAEO2Mat-codi8_tmx9wwIIWBM73fJryy155m_uhp95abX") can be seen when first booted up.

---

### Post by MyVitalRemains on 2012-08-17
I'm using the latest 12.04 version by the way.

---

### Post by oldfred on 2012-08-17
Do not know if this helps or not, has several suggestions and links to other suggestions:

[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/196239](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/196239)

---

### Post by MyVitalRemains on 2012-08-20
Well I tried all of the video card settings and the only one that worked without me having to put it on standby and back on was the *"i915.modeset=0"*. But even when I boot it with that setting, the resolutions lowers to VGA.

---

### Post by MyVitalRemains on 2012-08-23
Recently I posted a thread on this forum involving this issue, but I think that it will be best to create a new post with more information on it. 

After installing Ubuntu 12.04 and rebooting I came across an issue. Instead of seeing the usual Ubuntu screen, I see a blank purple screen when booting Ubuntu and a blank black screen when I booting Windows XP. The only way for me to access the OSes regularly is by me putting the computer on standby and back on. After doing this they work normally. 

All of the advise that I get involves adding certain things to the /etc/default/grub.conf file. I have tried adding "radeon.modeset=0", "xforcevesa", "nomodeset", "nouveau.modeset=0", "i915.modeset=1", "i915.modeset=0", and "radeon.modeset=0" to the "quiet splash" text in the .conf file and at times I even deleted the quiet splash lines and just added the text in quotations into it. But most of the time I either ended up with the blank purple screen (on Ubuntu) or have Ubuntu in VGA instead of the native 1024x600 resolution. 

So I think that it would be best to give you the laptop model and specifications. > 
[B]Model: Acer Aspire One D150 
[/B]CPU Intel Atom N270
Cache L2 cache - 512.0 KB
Front Side Bus - 533.0 MHz
Chipset - Mobile Intel 945GSE Express 
Graphics Processor - Intel GMA 950
[More info here]("http://www.cnet.com/laptops/acer-aspire-one-d150/4507-3121_7-33517218.html") 
Any help with this issue will be helpful. Thanks for reading!

---

### Post by sffvba[e0rt on 2012-08-24
*Threads **merged**.*

No point in getting the same advice that didn't work, now people that want to help have some more info to go on.


404

---

### Post by MyVitalRemains on 2012-08-24
Okay, thanks.

---

