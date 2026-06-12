---
title: "How To : Change AMD driver via Terminal 13.04"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by aaron-huddleston30 on 2013-10-17
Hey guys.  I figured out why my system is not booting the GUI, just sits at the pink screen but never loads the GUI for Ubuntu 13.04.  Pinpointed it to the official AMD drivers that I have switched to twice now.  This has happened before, and I never figured it out and just reinstalled everything completely.  This time, I noticed it bricked when I changed the drivers to the official drivers ( in additional drivers tab system settings ) for my video card.

So, now that I know this, if I am able to simply switch to the Ubuntu drivers for my AMD card, it would then load the GUI.  So how can I do this within the terminal?  I can get into Recovery Mode, open networking and then get into a terminal, but what then?

I have seen some things talking about jockey-text --list showing what driver is currently in use, but how can I use terminal to actually disable my current driver ( if needed ) and then move to another driver?

Thanks!

---

### Post by aaron-huddleston30 on 2013-10-19
Can't be done I guess?

---

### Post by QIII on 2013-10-19
Hello!

How did you install the driver?

---

### Post by aaron-huddleston30 on 2013-10-19
Via the Advanced Driver's ( additional drivers? ) option within the GUI.  It worked fine, until I rebooted and now the GUI will not load, just hits the pink screen and never loads the GUI.

---

### Post by QIII on 2013-10-19
Before you rebooted, did you do

```
sudo amdconfig --initial
```

---

### Post by aaron-huddleston30 on 2013-10-19
Hmmm, did not know that was a requirement.

---

### Post by QIII on 2013-10-19
It isn't *supposed *to be any more, but let's see if that helps.

You can run it from the terminal in recovery mode.  Do that, reboot and let me know if it helps.  Otherwise, we can move on.

---

### Post by aaron-huddleston30 on 2013-10-19
Hmm tried that and it just said no supported adapters detected

Sorry it took so long.  My keyboard likes to take awhile to turn on sometimes during reboot lol.  Took 4-5 tries before it finally came on before it auto-booted Ubuntu.

---

### Post by QIII on 2013-10-19
No supported adapters found sounds like the driver is not currently installed.  What model is your GPU?

Let's get you back to the open source driver for now.

First, in case there is an xorg.conf, rename it (the open source driver no longer needs an xorg.conf, and having one present can cause problems.)  If this gives you a message about the file not existing, don't worry about it.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
```

Then uninstall the driver

```
sudo apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

And you may need to reinstall these:

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

You should be able to reboot into Ubuntu with the default open source driver.

---

### Post by aaron-huddleston30 on 2013-10-19
Hey here I am reporting live from inside Ubuntu!  

Ahhh my precious Workspaces.  Thanks QIII!  I will keep that sheet around with the commands in case something like that happens again.  I had a strong feeling it was the dumb AMD drivers that did it.

Have they figured out what it is about those AMD drivers that kill the GUI like that?

BTW my system setup is :

I5-2400 @ 3.1Ghz - Quad Core
Radeon 6770 - 1GB @ 950Mhz OC
8GB DDR3 @ 1600Mhz

---

### Post by QIII on 2013-10-19
I've been using the drivers for years.  

If the open source driver works, however, I would recommend using it.  If you ever do need the proprietary driver, you can install it later.  I have a section on how to do it from the command line in the ATI driver wiki link in my signature.

For now, just enjoy using the open source driver and have fun!

---

