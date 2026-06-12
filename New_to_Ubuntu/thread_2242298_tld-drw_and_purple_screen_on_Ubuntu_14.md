---
title: "tld-drw and purple screen on Ubuntu 14"
date: 2014-09-01
forum: New to Ubuntu
---

### Post by andrew147 on 2014-09-01
So I recently got fed up dealing with Windows 7 and reconfigured my desktop to Ubuntu 14.  Everything seemed to be working fine, so I started adding programs.  I found this [http://scienceblogs.com/gregladen/2014/04/24/10-or-20-things-to-do-after-installing-ubuntu-14-04-trusty-tahr/](http://scienceblogs.com/gregladen/2014/04/24/10-or-20-things-to-do-after-installing-ubuntu-14-04-trusty-tahr/) list of add-ons and added a few.  When I got to the fan optimization bit, tld-drw, things went downhill fast.  My screens froze up and I had to restart.  When I restart, it goes to the purple screen and then stops.  If I go to the recovery boot, then finish the standard boot, things work fine (though the resolution seems a bit off and my monitors are duplicated rather than extended, but I think I can fix that later.)  I tried uninstalling the offending program, but it doesn't seem to work.  I still need to do my workaround to get it to boot.  Any thoughts?

ETA: I found another bug as well.  No sound.

---

### Post by ThatBum on 2014-09-01
You mean [FONT=courier new]tlp[/FONT] and [FONT=courier new]tlp-drw[/FONT]? You can uninstall them with [FONT=courier new]sudo apt-get autoremove tlp
[/FONT]
It's weird, I have tlp on my netbook and it works fine. All it seems to do is enable some hardware-level power saving settings when the netbook is on battery. Might have been caused by something else on that list. Then again, said power savings could be adversely affecting the video subsystem.

---

### Post by andrew147 on 2014-09-01
Well, that was just the one I installed when it started freaking out.  To be safe, I've uninstalled everything on that list that I'd installed previously.  Still hasn't fixed it.

ETA: Decided to try one last reboot before I hit the hay.  AND IT WORKED!  Sort of.  Autoremove must have found one last straggler that had been screwing up my install.  Still no sound.  But it boots normally now!

ETA: And a second reboot fixed the sound issue.  I don't know why, I don't really care, it's nearly 2 a.m. and my computer's not broken anymore.  I'm opening the champagne.

---

### Post by ThatBum on 2014-09-01
That's good. Try hitting your sound icon and viewing Sound Settings, and see if it even still recognizes your sound hardware.

E: Glad to have been of help.

---

### Post by grahammechanical on 2014-09-01
For information only.

When we use Recovery>Resume in 14.04 we load to a desktop with an open source video driver call llvmpipe. It is used in Ubuntu primarily as a fall back video driver for graphic adapters that do not do hardware 3D acceleration but it is also used with the Resume option. So, that is the reason for the less than expected video experience. But it can get us to a working desktop where we can fix things. May be. And a reboot will load the normal video driver.

Regards.

---

