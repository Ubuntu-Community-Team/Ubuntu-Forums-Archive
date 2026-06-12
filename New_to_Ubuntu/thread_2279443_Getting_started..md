---
title: "Getting started."
date: 2015-05-23
forum: New to Ubuntu
---

### Post by regdabs on 2015-05-23
Decied to try ubuntu yesterday and installed using WUBI, seemed to work OK.  But now when I try to log in I enter the user name and password
I used during setup, but it tells me the passwork is invalid, even though I know it is correct.  If I try to get on as guest it won't let me set up
WI-FI account without root password, ( I don't know what that is). Any help or suggestion as to what I am doing wrong, I just started and am
lost right now.

---

### Post by yancek on 2015-05-23
On a normal install of Ubuntu, you are required to create at least one user with a password.  That user would have root permissions.  I've never used wubi so I don't know if it works the way a normal install does but I would expect it to.  Check the link below.  Wubi isn't supported and is not expected to work with windows 8.  If you have an earlier version of windows it might work.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by ajgreeny on 2015-05-23
Just out of interest, does your username chosen at installation start with a capital (upper case) letter?

Even if that is what you typed in the username box when installing the system your real username will be all lower case letters, so, for example, if you are trying to use **Regdabs** as username try **regdabs** instead in the login box, and don't forget that Linux is case sensitive for passwords, (except usernames as explained above) so **Password** is different from **password**.

If still no go try logging in at command line in case this is a GUI only problem:-
Use Ctrl+Alt+F1 at login acreen
Login by typing username, which will show on screen, and password, which will not show on screen; just type and hit enter.

---

### Post by Adam_Kleiner on 2015-05-23
Yes, I second what yancek said. I'd like to add that probably your best best would be to go pull the standard image from Ubuntu's official website. Specifically, any computer using Win8 or above is likely going to use UEFI, which doesn't play nicely with other operating systems. The official images have measures in place to help work around UEFI, so I strongly recommend that you back up any important data and start over with the official image. Even if we're talking about a computer without a DVD drive, you can always use a USB drive and UNetBootin.

---

### Post by RobGoss on 2015-05-23
Make sure you're entering the correct  credentials, I remember when I first started with Linux I wasn't use to login with a user name because In Windows all we need is our pass word and were in. So not knowing any better when I try to login is was asking me for a user name but I was entering my pass word  instead and could not get in to my machine unti I realized what I was doing wrong.

---

### Post by regdabs on 2015-05-23
Login is all lower case, no Caps.  I am running windows 7 so that shouldn't be a problem.  I have uninstalled and re-install twice same results all 3 times.  It installs ubuntu 13.04 I think, not looking at it right so not sure, but that is what WUBI installs. I do have a DVD drive.

---

### Post by Vladlenin5000 on 2015-05-23
Now there are two things you shouldn't be doing: WUBI and installing and EoL, hence unsupported, version.

If doable, please install a supported version in dual-boot, never WUBI.

---

### Post by hakuna_matata on 2015-05-24
> **regdabs said:**
> It installs ubuntu 13.04 I think, not looking at it right so not sure, but that is what WUBI installs.
IMHO it is an old bug: bug [1155704]("https://bugs.launchpad.net/wubi/+bug/1155704")

That means that you use an old Wubi version which downloads an old development release of 13.04. It makes really no sense to repair this install.

Is there a special reason for using Wubi ?

---

### Post by Vladlenin5000 on 2015-05-24
> **hakuna_matata said:**
> Is there a special reason for using Wubi ?

Tradition/inertia, perhaps?
The "decided to try Ubuntu yesterday" must be put in context... When was "yesterday"? In 2008? -> [http://ubuntuforums.org/showthread.php?t=763242](http://ubuntuforums.org/showthread.php?t=763242)

At this point I'll be blunt: Following the forum policy I'm neither helping with WUBI nor any EoL version. No one else should:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

regdabs, if you want help to install a proper dual-boot with a currently supported Ubuntu version, we can help. <snip>

---

