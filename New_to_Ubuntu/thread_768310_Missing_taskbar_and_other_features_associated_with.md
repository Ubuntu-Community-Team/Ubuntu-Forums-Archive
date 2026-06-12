---
title: "Missing taskbar and other features associated with it on Kubuntu Hardy Heron (8.04)"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by keith11 on 2008-04-26
Hi,

I was enjoying Hardy Heron and I installed the battery monitor for my Lenovo X61t tablet. I also installed Firefox 3. After I installed them, I got some error message regarding Plasma; I am not sure what it was, but after the error message, the taskbar panel at the bottom of the screen just disappeared. I don't know how to get it back - I have tried logging on and off, restarting, etc, but it doesn't work. I can login as root and under root login, the taskbar panel is there on the desktop. What can I do to get the taskbar panel back under my normal user access?

Other than this, when the taskbar panel was working, I didn't see options to add a lot of applets like Gutsy had. I did not even see options for locking or unlocking the taskbar panel. Is it becuase I am running KDE 4? I appreciate any help regarding this. Thanks.

Keith.

---

### Post by keith11 on 2008-04-26
Bump! Well, I am hoping I can get some help soon so that I can again log into my kubuntu installation. Thanks.

Keith.

---

### Post by set117 on 2008-04-30
> **keith11 said:**
> Bump! Well, I am hoping I can get some help soon so that I can again log into my kubuntu installation. Thanks.

Keith.

Keith, I have the EXACT same problem.  The first time I logged in, all good, I shut down the computer, restarted at a cafe, and no more taskbar.  I have had to put the Menu Bar icon on my desktop and load up Avant Window Navigator to make my desktop even usable.

I am not sure if this helps, but this happened after I upgraded from Gutsy to Hardy, and then upgraded KDE from KDE3 to KDE4.  Like I said, the first time I started up, everything was fine, but on every subsequent startup the taskbar has been missing.

Shane

---

### Post by set117 on 2008-04-30
> **keith11 said:**
> Bump! Well, I am hoping I can get some help soon so that I can again log into my kubuntu installation. Thanks.

Keith.

Keith!

   I found a solution that worked over on at the Suse forums!  Here is the link: [http://forums.suselinuxsupport.de/index.php?showtopic=64771](http://forums.suselinuxsupport.de/index.php?showtopic=64771)

I did what it said, which is:

"went to ./kde4/share/config and deleted the plasma* files. loged back in and i got my taskbar back."

Doing a normal logout only rewrote the plasma* files, I had to delete those files, and do a CTRL-ALT-BACKSPACE to completely reset X (also logging out) so that the files would not be re-written.

Shane

---

