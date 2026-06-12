---
title: "Are there install problems with 13.04?"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by Crossbow on 2013-06-02
Hi - I am asking this in the Absolute Beginners forum because I am seriously computer illiterate.

My upgrade from12.04 to 12.10 was a NIGHTMARE. I could not get my GUI back, could not even log in except in recovery mode, and it's still not booting up correctly. I have an Nvidia graphics card, I was previously using Nvidia-173 but I could not get ANY Nvidia version to work. I ended up installing something called FGLRX, do not even really understand why, but it works OK. I have a GUI now. But the whole mess takes forever to boot up and always boots to the grub menu no matter what I do. I looked up 12.10 problems AFTER I tried to upgrade, like an idiot, and found other people had a problem with it hanging up halfway through the install, and there were a million different workarounds, not one of which worked for more than one person apparently. 

Up until 12.10, I had always gotten the latest Ubuntu by just clicking on "upgrade," and everything was fine. Now I am afraid to upgrade again. I have searched the forums for "13.04" and "13.04 problems" but got nothing. I read some reviews and they all talked about how much faster 13.04 is, but none said anything about installation issues. Is it safe? Will it destroy my driver again? What else do I need to know?

---

### Post by deadflowr on 2013-06-02
Post the output for
```
lspci -v | grep VGA
```

Hopefully with the output, we will have a better understanding of the card you have.
And what best driver you could install, which won't cause you problems if you intend to upgrade.

Sidenote: the fglrx driver is an AMD driver, so why it helps you is beside me.

---

### Post by Frogs Hair on 2013-06-02
As always upgrades are working well for some and not for others . As for the driver I have no idea why that driver is working for you either because it is an AMD driver .  Having observed an from 12.10 to 13.04 upgrade I cant tell you that backup and and clean installation are much faster. It was not the download but rather package replacement and setup that took hours.
 
I have an older Nvidia card and the 1.73 driver  was garbage in my system back on 9.10 and I have used the Nvidia current or newer drivers. The default Nouveau works pretty well on 13.04. IMHO preform a clean installation if you have a choice. Check 13.04 system requirements if you have doubts about your hardware.

Edit: I should add that I have installed 13.04 three times with out any problems and one of the installations was the beta release.

---

### Post by Crossbow on 2013-06-08
I will give it a try. I am avoiding doing a clean install for two reasons: I don't want to backup all my photos, and the last time I tried to burn an Ubuntu disc I couldn't. I have done it before but for some reason it's not working with 13.4. 

```

anna@anna-desktop:~$ lspci -v | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8300 GS] (rev a1) (prog-if 00 [VGA controller])

```

---

### Post by Zill on 2013-06-08
> **Crossbow said:**
> ...I don't want to backup all my photos...
Then obviously your photos are not important to you!

Hard drives can, and do, fail without warning.  In addition, user "finger trouble" can destroy any or all of your data in seconds!

If you really don't want to lose your photos or other data then good backups are not *optional*, they are *essential*.  While a regular backup routine is best, at the very least you need to backup *before* major system work such as upgrading.

There are plenty of methods available to backup your data but I can strongly recommend [luckyBackup]("http://luckybackup.sourceforge.net/features.html"). It's in the repos.
```
sudo apt-get install luckybackup
```

---

### Post by Crossbow on 2013-06-08
Thanks.  I will check that out. I do auto back up with Dropbox but it is full, has been for months. I don't want to pay for more storage because I'm cheap. My roommate backs everything up on CDs so I took a shot at that but DAMN photos take up a lot of space!

---

### Post by 3rdalbum on 2013-06-08
1. In-place upgrades never work for 100% of the population. The closer you are yo "default" Ubuntu the greater your chance of success.

2. A clean install does not mean losing all your data. You should definitely back up your photos anyway, but if you boot the Ubuntu CD and run the installer, then choose "upgrade" as the method of installation, you will get a clean install that preserves your existing files.

---

### Post by Zill on 2013-06-09
Crossbow:  You can get a 1TB USB External Hard Drive for around GBP50 (approx USD80).  You need to decide if your photos and other data are worth this.

---

### Post by mastablasta on 2013-06-09
> **Crossbow said:**
> I will give it a try. I am avoiding doing a clean install for two reasons: I don't want to backup all my photos, and the last time I tried to burn an Ubuntu disc I couldn't. I have done it before but for some reason it's not working with 13.4. 

```

anna@anna-desktop:~$ lspci -v | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8300 GS] (rev a1) (prog-if 00 [VGA controller])

```

assuming you have nvidia drivers installed you need to first disable them, then do the upgrade and then install new graphics drivers.

---

### Post by Rob Sayer on 2013-06-09
I've done upgrade instead of installing a newer version before but from what I've read here of problems I think I'd prefer to just do a clean reinstall.  It's a good idea to back up data every day as you accumulate it.  I prefer to do it this way and treat system and data backup separately.  That's one reason I like linux so much more than windows, which does not encourage this approach.

For what it's worth, I have 13.04 on this netbook I'm typing this on and I had far more problems with 12.04 on it.

Before any upgrade or reinstall it's a good idea to search for any problems with the new version on your hardware, especially the graphics and wireless.

---

### Post by Crossbow on 2013-06-09
Installed luckybackup... still figuring out how to use it.

---

### Post by mastablasta on 2013-06-09
try backup with dejadup: [https://live.gnome.org/DejaDup/Screenshots](https://live.gnome.org/DejaDup/Screenshots), linuxmintbackup tool: [http://community.linuxmint.com/software/view/mintbackup](http://community.linuxmint.com/software/view/mintbackup) or backup the whole disk with an image using Redobackup live disk: [http://redobackup.org/](http://redobackup.org/).

these have the simplest interfaces available. not much to figure out with them...

---

### Post by Crossbow on 2013-06-10
OK, backup seems to have worked... I guess. Everything has green checks anyway... 
Install worked fine. Thanks guys.

---

