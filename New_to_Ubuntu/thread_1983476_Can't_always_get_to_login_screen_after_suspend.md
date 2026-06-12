---
title: "Can't always get to login screen after suspend"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by joetait on 2012-05-20
Hi, I am having some issues with getting logged back in after suspending on my laptop, any help/ideas would be appreciated.

I only suspend by putting the lid down, but I can't imagine this will affect it. Essentially, I can see a cursor, which I can move. The cursor will change to arrow/text/hand according to whatever it would be over based on the last screen I had (eg, if I had firefox on the screen before suspend, and I move to where the address bar would be it will change to a text cursor). However, the rest of the screen is black. 

I can access tty1-6. I can log on and do stuff, so if there is someway to reset via this that would be fine. Also, I can still turn the screen off via keybaord functions etc.

Any ideas would be great. Laptop is an Asus A52F, and I am running 12.04.

---

### Post by 2F4U on 2012-05-20
What is the graphics card and the driver you are using? And there is a difference between, for example, suspending from the menu and closing the lid. I have one laptop that just suspends right when I do it from the menu. Can you try if it makes a difference how you suspend?

---

### Post by joetait on 2012-05-22
> **2F4U said:**
> What is the graphics card and the driver you are using? And there is a difference between, for example, suspending from the menu and closing the lid. I have one laptop that just suspends right when I do it from the menu. Can you try if it makes a difference how you suspend?

Sorry for the delayed reply. The only output from lspci that looks relevant is
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

```

I am not sure how to find out which driver I am using, but it certainly is not proprietary, as I do know how to check for that.

It seems to be okay when I suspend normally, but it is kind of random anyway, so I cannot 100% confirm this. In your experience, does suspending normally, then closing the lid, work fine? Or did you have to leave the lid up?

---

### Post by skyw33 on 2012-05-22
I have the same problem.  Ubuntu 12.04, Lenovo G560. 

lspci:  00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

uname -a:  Linux computer-name 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Pi-Rat on 2012-06-15
I'm having  a very, very similar issue. It doesn't always happen and I haven't been able to intentionally replicate the problem. Doesn't seem to matter if suspended from the menu or by closing the laptop lid. Sometimes the screen is totally black, but the mouse will change to a text input cursor. Other times, the desktop wallpaper shows, but nothing else. Only way to get out of that is to force it to restart by holding down my power button.

System details:
Ubuntu 12.04, Toshiba Satelite A205-S5814 model# PSAF3U-0P900V
lspci: 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
uname -a: 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:33:05 UTC 2012 i686 i686 i386 GNU/Linux

Mine system is roughly 4-5 years old,I think. How old are your systems? Do we all have a common batch of motherboards maybe? :-k

---

### Post by xxrsc on 2012-08-07
Same problem here.

> Ubuntu 12.04

Dell Inspiron N5030

Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

3.2.0-27-generic

---

### Post by sandyd on 2012-08-08
Its a bug.
Its been filed a while back now.

I can't find the link though.

---

### Post by sandyd on 2012-08-08
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1021035](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1021035)

---

