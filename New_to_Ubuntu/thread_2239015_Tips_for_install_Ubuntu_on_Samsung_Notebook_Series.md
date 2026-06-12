---
title: "Tips for install Ubuntu on Samsung Notebook Series 5 - NP550P5C-AD1BR"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by Allan_ on 2014-08-11
Hello Everybody,

I need install Ubuntu on my Samsung Notebook Series 5 - NP550P5C-AD1BR. I have installed windows 8. 

I read some things and I have one doubt if my notebook is compatible with Ubuntu, if all drivers will work well. 

My notebook have 2 video card (Intel HD Graphics 4000 and GeForce GT 630M) and I read that nvidia optimus dont work well on Ubuntu, this is true ?

For now I want make a dual boot, for make some testing with Ubuntu. If everything works fine I will delete Windows of my life :p

Thanks for help.

---

### Post by Jonathan Precise on 2014-08-11
Get a free copy of ubuntu at [www.ubuntu.com/download]("http://www.ubuntu.com/download"). Make sure you selected 64-bit ubuntu. [Check if the md5sums match]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_with_.22Checksums_calculator.22") and burn it to a DVD (Make sure to select "Burn image" or similar option, or it will fail to work). Reboot, and you should get a GRUB menu. Select "Try Ubuntu". If it works, then It should be able to run ubuntu. Play around with it, and if you decide you want to install as a dual-boot scenario, double-click install ubuntu, and follow the instructions.

Hope it's of help! :)

---

### Post by Allan_ on 2014-08-13
Thanks for your Help Jonathan ! Another doubt : I have 200GB free space on my HD. How is the best partition division ?

---

### Post by chris272 on 2014-08-13
Ubuntu well ask you how you want to partition it, and even make a suggestion. It's so easy with ubuntu.

---

### Post by bradwilliams923 on 2014-08-13
Just be sure to set a swap partition. Advice goes back and forth on whether it should be equal to your system's RAM or double it, and whether that changes based on whether you're using 32-bit or 64-bit Linux, but a quick google search should inform you. If you let Ubuntu set up partitions for you, you can disregard this message, but if you do it yourself, just make sure to set one.

---

### Post by Rob Sayer on 2014-08-13
What you do with the swap partition does not depend on whether you have 32 or 64 bit whatsoever, and unless you need hibernate capability stick to the default swap setup.  And everything else except for the size of the linux partition in a dual boot setup of course.

The only exception I'd make would be to install with a separate partition for the /home folder, which is incredibly useful because you can upgrade/reinstall without losing your data or user settings.  It's faster too.

I wouldn't say that nvidia is necessarily problematic but it can take some config.  A dual gpu situation is more complex to configure.  Search "ubuntu <gpu card models>".

Stick to ubuntu support sites, and be careful of blogs.  Some are good.  Others make me wonder how someone with such a poor grasp of linux fundamentals could actually think they were qualified to write on the subject.  This is a web disease and noobs can't tell the difference.

---

### Post by Allan_ on 2014-08-14
Hi Guys ! I can't install Ubuntu 14.04 with dual boot because instalation says that not detected installed S.O. on my computer. So I erase all and install ubuntu :p For now everything is working as well. Can you give me a few basic steps for start using ubuntu ? like install flash player. Thanks for help ! Sorry my english !

---

### Post by Jonathan Precise on 2014-08-14
I recommend you install ubuntu-restricted-extras. You can search for it in the software center, or you can do it the fast way. Press Ctrl-Alt-T, and type this into the terminal:

```
pkexec apt-get install -y ubuntu-restricted-extras
```

---

### Post by Allan_ on 2014-08-14
What must happens when I type this ???

---

### Post by Jonathan Precise on 2014-08-14
If you do not like the default desktop, see the picture.  If you like it, install Gnome 3:
[ATTACH=CONFIG]255484[/ATTACH]

```
pkexec apt-get install -y gnome
```

[HR][/HR]

If you don't like it, you can install just the old gnome (see the pic). If you like it, install Gnome Flashback:
[ATTACH=CONFIG]255485[/ATTACH]

```
pkexec apt-get install -y gnome-flashback
```

Don't like any of them? Try XFCE/Cinnamon/MATE/LXDE. (Google them up.)

---

### Post by Jonathan Precise on 2014-08-14
> **Allan_ said:**
> What must happens when I type this ???

There are some proprietary codecs not included in ubuntu by default, due to copyright issues. You may have been offered them during the install. If you did not choose to install them, then you must install them manually, as I mentioned. It's better to live with them, as some stuff may not work without it, like some video files not playing, some DVDs not playing, etc.

[hr][/hr]

I also recommend installing Google chrome from [here]("https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb"). It's a fast and secure browser from Google, and comes with flash preinstalled. If you prefer it over FF, then you can download it [here]("https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb").

---

### Post by Jonathan Precise on 2014-08-14
Before installing chrome (if you install it), I recommend you please install GDebi:

```
pkexec apt-get install -y gdebi
```

Right-click the downloaded google-chrome-stable_current_amd64.deb, select properties. Go to the "Open with" tab, and make GDebi the default. Then you can proceed.

---

### Post by Allan_ on 2014-08-14
Thanks Jonathan for your help ! Now I can watch videos on youtube :D  I LIKE the GNOME 3 and I will install.

---

### Post by Allan_ on 2014-08-14
Jonathan I'm installing he code bellow and my doubt is what gdm I select ? 

gdm or Lightgdm ?

pkexec apt-get install -y gnome

---

### Post by Rob Sayer on 2014-08-16
I'm not quite sure where this idea to use pkexec to install comes from.  Pkexec is meant to access other user's accounts.  Everyone else uses sudo for installing.  I've *never* used pkexec and see no reason to start.

Here's something about pkexex v. sudo:

[http://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo](http://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo)

and if you don't understand that use sudo.

---

### Post by Jonathan Precise on 2014-08-16
I'm just saying to use pkexec as it's graphical, and it's the one I always use. You can use gksu as well.

---

### Post by Jonathan Precise on 2014-08-16
> **Allan_ said:**
> Jonathan I'm installing he code bellow and my doubt is what gdm I select ? 

gdm or Lightgdm ?

pkexec apt-get install -y gnome

Please select LightDM. If you select gdm, the login screen will change.

---

### Post by Allan_ on 2014-08-21
Thanks for help guys ! Ubuntu working fine here !

---

