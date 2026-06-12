---
title: "How do I roll back my system from an exploded driver?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Vunutus on 2008-12-01
I used the Hardware Drivers utility to download a new driver for my video card. It finished installing and wanted to reboot my system. Upon rebooting, my video is completely broken. As soon as it tries to start rendering graphics, my monitor goes blank with a "No Signal Input" type error.

How can I uninstall the driver from the command line, and for that matter, how do I switch to run level 1 from grub to work at the command line? If the solution requires the internet, it must be something I can download in Windows and put on a thumbdrive. I have dialup with an external USB modem, and none of the command line ppp utilities support it. I can only dial with gnome-ppp, which I doubt will work on the command line.

---

### Post by hyper_ch on 2008-12-01
(1) select recovery mode at startup

(2) login

(3) run:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg -phigh

```

---

### Post by anewguy on 2008-12-01
Without exactly seeing it I can give you some general advice:

Unlike Windows, for a video driver you do not actually need to remove it or roll back.  There is a file called xorg.conf which holds the configuration settings for X Windows, and I suspect this is causing your problem.  Normally a video driver update adds a driver file (or more) for xorg and modifies the config file to reflect that driver.  Here's what I would do:

log in to a terminal window (either command line at boot or ctrl/alt/F1 otherwise)

type:

su <enter> -> use your normal password

cd /etc/X11  <enter>

ls -al xorg.con* <enter>

you should see an xorg.conf file and perhaps a xorg.conf~ file.  You can try just copying the back up (the ~ file) back to the original:

cp xorg.conf~ xorg.conf <enter>

then reboot:

from the command line:  shutdown -r now <enter>

See if your video returns.  If not:

log in to a terminal window

type:

su <enter> -> enter your regular password

cd /etc/X11

gedit xorg.conf

search for a line something like "nv", "nvidia", "ati", "fglrx" or some other variation in a device section (it defines your video adaptor and driver).  Change this to "vesa", save the file, exit and reboot.

Dave :)

---

### Post by hyper_ch on 2008-12-01
ane: su does not work... this is ubuntu and it uses sudo ;)

---

### Post by anewguy on 2008-12-01
su on it's own works - asks for a password, then you are put in superuser mode.

Dave :)

---

### Post by hyper_ch on 2008-12-01
only if you enabled root - which isn't the case normally.

---

### Post by anewguy on 2008-12-01
Oooppss - I have did enable root (my bad!) :)

Dave :)

---

### Post by phidia on 2008-12-01
If you listen closely you'll hear even more air escaping from your ballon.
Why? Because if this is the latest release-8.10 you can't edit /etc/X11/xorg.conf
The configuration for video and monitor isn't there anymore.

---

### Post by Vunutus on 2008-12-01
> **phidia said:**
> If you listen closely you'll hear even more air escaping from your ballon.
Why? Because if this is the latest release-8.10 you can't edit /etc/X11/xorg.conf
The configuration for video and monitor isn't there anymore.

Luckily I'm on 8.04, I hope it doesn't have the same problem :)

I haven't tried either of the fixes here yet, but I have them sitting on my desk for when I'm done with this paper. Hopefully they work :D

---

### Post by bwang on 2008-12-01
The configuration in xorg.conf doesn't seem to be there in Hardy either. I wonder why they took it out? It makes it rather hard to fix issues with the X Server.

---

### Post by phidia on 2008-12-01
> **bwang said:**
> The configuration in xorg.conf doesn't seem to be there in Hardy either. I wonder why they took it out? It makes it rather hard to fix issues with the X Server.

I've been saying this, as have a few others here, for some time now.
Yes 8.04 has the problem too (xorg 7.4) although it sometimes responds to adjustments better IMO.

The official way to fix X now is to boot in recovery and type "xfix".
If that doesn't work then you need to stay with windows until you can buy newer hardware. 
No I'm not kidding see post number 12 [here]("http://ubuntuforums.org/showthread.php?t=995159&page=2").

---

### Post by anewguy on 2008-12-02
> **phidia said:**
> If you listen closely you'll hear even more air escaping from your ballon.
Why? Because if this is the latest release-8.10 you can't edit /etc/X11/xorg.conf
The configuration for video and monitor isn't there anymore.

Still 8.04 lts for me, but thanks for the heads up.

---

### Post by anewguy on 2008-12-02
> **phidia said:**
> If you listen closely you'll hear even more air escaping from your ballon.
Why? Because if this is the latest release-8.10 you can't edit /etc/X11/xorg.conf
The configuration for video and monitor isn't there anymore.

FYI - I installed 8.10 via the update, and my xorg.conf file is still there with my video card and driver defined and both of my monitors defined so I get my dual monitor setup.  EDIT:  I set xorg.conf back to the defaults (no device or monitor) and I lose both my driver (the screen is messed up) and my dual monitors.  I can only conclude that even though the devices may not by default be definded in xorg.conf, that it still works like 8.04 -> you can add your monitors and adaptors to get your driver(s) and monitors working (in my case, the dual monitors).

As far as 8.04 and a missing xorg.conf file goes, it may be missing, but you CAN create it and it does matter - that's what I had to do to define my video card and monitors to get my dual monitors to work.

Dave ;)

---

### Post by phidia on 2008-12-02
anewguy, That has not been my experiance. I tried to use an exact copy of a working xorg.conf from a previous release with 8.10 and it definately didn't work, but good that you got it going.

---

### Post by anewguy on 2008-12-03
> **phidia said:**
> anewguy, That has not been my experiance. I tried to use an exact copy of a working xorg.conf from a previous release with 8.10 and it definately didn't work, but good that you got it going.

There may be something else that is in your xorg.conf that is not compatible.  If you'd like, I could post my xorg.conf - obviously somethings will be different, but perhaps it might point you towards another option.

Dave ;)

---

### Post by phidia on 2008-12-03
Thanks my "option" is to use 7.10 and mepis neither of which exhibit user unfriendly xorg configuration.
Maybe future updates will correct this but I've seen many machines that failed to load x under 8.04 and/or 8.10 whereas previous releases worked.

---

### Post by anewguy on 2008-12-03
Sounds good - obviously we all need to do what ever works for us.  If you don't know, if you are using a video driver not officially supported by Ubuntu, such as the ATI or NVidia drivers loaded by envy (envyng for 8.04 and 8.10), you will need to reinstall them after the upgrade.  Obviously if it was a from-scratch install you need to reinstall them as well.  Envy (or envyng) will update your xorg.conf file for you and it usually seems to work quite well.  Given your experience, I assume you already know that, but I wanted to post it here in case others not as knowledgable are reading this thread looking for a solution.

Have a good one!

Dave ;)

---

