---
title: "After purging and reinstalling fglrx, keyboard and mouse don't work"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by lifelike27 on 2011-11-28
This is regarding Ubuntu 11.04

So I tried to install the open source ATI graphics drivers by removing the proprietary ones (fglrx) and I ended up loosing xserver completely. Using one of the wikis on Ubuntu, I was able to remove everything stupid I did and reinstall the ATI proprietary graphics again (10.8 driver)

Now, when I get to the login screen, my mouse and keyboard don't work at all, not even a usb keyboard and mouse.

Does anyone have any idea how to fix this? I really need my linux machine working before my finals. It's required!


I would really really absolutely completely worship the person who could help me with this! :D

---

### Post by Sealbhach on 2011-11-29
Log in with recovery mode (choose it at the Grub screen). Then select root shell with networking. Then when you are at the command line prompt do

```
sudo apt-get install --reinstall xserver-xorg-input-all
```

This will reinstall all your input drivers and hopefully after you reboot the problem will be solved. You need a wired connection to have networking in enabled in recovery mode so make sure you have the cable plugged in.

.

---

### Post by lifelike27 on 2011-12-01
Hello,

Thanks for the reply. Unfortunately that doesn't seem to work.

At first it said that there was some error and I should run 'sudo apt-get -f install'. So I did that, and then re-ran the command above and it didn't seem to work after I restarted...

---

### Post by lifelike27 on 2011-12-07
*bump*

Any other suggestions guys? I'm pretty sad that I can't use Ubuntu, I have to use Windows 7 because of this..

---

### Post by pme 72 on 2011-12-07
Maybe try running Update Manager. Worked for someone else recently who lost keyboard and mouse functionality when purging fglrx.

---

### Post by lifelike27 on 2011-12-07
> **pme 72 said:**
> Maybe try running Update Manager. Worked for someone else recently who lost keyboard and mouse functionality when purging fglrx.

Could you link me to that thread if possible as well? I'll try updating as soon as I get home.

---

### Post by lifelike27 on 2011-12-08
pme 72,

I ran update manager and unfortunately it didn't help. So I followed the [wiki]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver") to purging the driver and reinstalling it. That went fine - tried updating after that too, didn't work.

My graphics is working fine, it's just my keyboard and mouse that aren't working at all! 

I'm using the 2.6.39 kernel, I also have the 2.6.38-8 and that shows similar problems, the only difference is that plymouth is stretched and of a lower resolution than on the 6.39 kernel.

I feel like I'm so close to getting this!

---

### Post by pme 72 on 2011-12-08
It was really just a shot in the dark. The original post was from someone on 10.04 with an older unsupported card who installed fglrx and got a black screen. 

[http://ubuntuforums.org/showthread.php?p=11462872#post11462872](http://ubuntuforums.org/showthread.php?p=11462872#post11462872)

Have you looked through the 11.04 Installation Guide for ideas?

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

---

### Post by lifelike27 on 2011-12-20
So I was finally able to look at the wiki (I had finals), and I removed any existing fglrx drivers and installed a new one just like the wiki showed. Everything worked out fine.

Then to test it out I ran fglrxinfo and it spit out 'Error: unable to open display (null)'

According to the ATI Radeon driver wiki [here]("https://help.ubuntu.com/community/RadeonDriver") running 'lspci -nn | grep VGA' should give something like this:```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

```

However, for me, it doesn't show anything...

I think I need another stepping stone in the right direction again..

---

