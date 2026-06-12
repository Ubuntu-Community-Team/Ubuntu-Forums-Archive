---
title: "Dell Inspiron 1100 - Start Up Issues (No Graphics/Black Screen)"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by the_good_rev on 2008-05-25
I have seen a thread like this more times than I care to with no resolution in sight.  This leads me to believe that the problem cannot be solved.  Outlining the details, I have a Dell Inspiron 1100 that I recently removed Windows from and installed Ubuntu 8.04.  I love it!  What I don't love is the inconsistency of my system.  Sometimes it will boot up and a black screen will be the only thing I see, while I hear the drum in the background waiting for my username and password (you can log-in just fine, but no visuals).  Other times, nothing will happen...just a black screen.  I really don't know all the different commands and things, so any help I can get for this situation would be great!

---

### Post by beeman1266 on 2008-07-21
I have the exact same problem as you. Total newb as well. I've tried to do some of the fixes suggested, like upgrade to BIOS 32 and switch the video memory from 1 GB to 8 GB but I still get the blank screen problem. This guy ([http://ubuntuforums.org/showthread.php?t=819541&highlight=hang-over+inspiron](http://ubuntuforums.org/showthread.php?t=819541&highlight=hang-over+inspiron)) has some strong feelings about this. He suggests installing ubuntu 7.10 instead. He also provides a step by step guide to do this.

---

### Post by m_ad on 2008-07-21
I had the same problem with one of my computers, due to small amount of RAM. how much do you have?

---

### Post by ET! on 2008-07-22
try this link


[http://ubuntuforums.org/showthread.php?t=859118](http://ubuntuforums.org/showthread.php?t=859118)

---

### Post by jbrax on 2008-10-20
If you get blank screen after every other boot **change splash to nosplash, line 89 in /boot/grub/menu.lst**. 

If you have already updated the kernel you have to change "splash" to "nosplash" manually in every existing kernel line too. Line 89 changes the default so that every new kernel will get "nosplash" attribute. 

For more detals see my comment at [http://ubuntuforums.org/showthread.php?t=819541](http://ubuntuforums.org/showthread.php?t=819541)

How to edit menu.lst? Open terminal and type: gksudo gedit /boot/grub/menu.lst

---

### Post by ladybugderby on 2009-01-07
Had an Inspiron 1100 and had the same problem with the blank (or sometimes tan) screen.  I tried the fix mentioned at [http://ubuntuforums.org/showthread.php?t=807351](http://ubuntuforums.org/showthread.php?t=807351), and it worked brilliantly, at least for some time, and at least for regular boots (i.e., not when the computer went into "suspension" or hibernation).

---

### Post by ladybugderby on 2009-01-07
The fix had something to do with removing "compiz special effects."

---

### Post by ladybugderby on 2009-01-08
BTW, thanks jbrax for your post above.  Very manageable to follow.

---

### Post by skselby on 2009-12-09
Just a quick update for Karmic users - menu.lst no longer exists as Karmic is using Grub2.  Instead, update line 9 in /etc/default/grub to set splash to nosplash and then run update-grub.

Worked for me!

---

### Post by srf21c on 2010-01-11
> **skselby said:**
> Just a quick update for Karmic users - menu.lst no longer exists as Karmic is using Grub2.  Instead, update line 9 in /etc/default/grub to set splash to nosplash and then run update-grub.

Worked for me!

Werd up, thx for providing updated info for releases using Grub2, this worked like a champ for me as well.

---

### Post by jruberto on 2010-02-24
Most folks will probably corroborate that any of these proposed fixes may seem to work for a minute or two, but you'll still have the problem intermittently.

I've found a solid solution (applies to 9.10):

add[INDENT]**[FONT=Courier New][SIZE=3] i915.modeset=0[/SIZE][/FONT]**
[/INDENT]as a grub boot option (put it right after nosplash)

This will prevent the boot loader from switching video modes before X loads..  Any text-mode stuff that happens outside of X (ctrl-alt F2 terminals for instance) will be in a little 640x480 box in the middle of the screen, but that is a very small price to pay for getting your system to boot correctly every time!  (imo)

Other fixes I have in place:

[LIST]
[*]Bios upgrade to A32 & set video memory to 8MB
[*]nosplash boot option.  honestly not sure if this has any effect, with the i915.modeswitch fix in place i bet you can safely go back to splash but i'm not curious enough to try it.
[*]Revert to intel 2.4 video driver to fix random freeze in X (also seemed to give a performance boost) [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
[*]Completely remove compiz using package manager. ( Iexperienced a great increase in video performance after removal, even though it was disabled in System | Appearance | Visual Effects)
[/LIST]
 
FINALLY no more video problems and I'm even happily using power management features, tho suspend is still dodgy.

Cheers, j

---

### Post by jruberto on 2010-02-24
hope this helps someone. :D

---

### Post by jruberto on 2010-03-02
STILL experiencing the occasional "blank screen at boot" and have found yet another solution in addition to the above. I arrived at this conclusion by rebooting until getting the blank screen, then connecting via SSH and seeing what could bring the screen back. Conclusion is to add the following commands to the end of **/etc/gdm/Init/Default**, right before the final exit 0... I have not had a blank screen since doing this, with many cold and warm reboot tests:

```
/usr/sbin/vbetool dpms off
/usr/sbin/vbetool dpms on
```The first command seems to be necessary for the second one to work.

Also, I tried going back to "splash" and removing the "i915.modeset=0" and they are both still required.

---

### Post by MikeG0 on 2010-05-27
jruberto, tried all those settings and still am getting random crashes.
I upgraded to 10.04.  Still no luck.  The most recent bug entry is ... [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/578167](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/578167)

seems to be a problem with the intel i845g driver.  Our only hope is to  get a lot of people subscribed to this bug and get it fixed.  It's been around for a while and affects a lot of distros.

Best regards,

Mike

---

### Post by MikeG0 on 2010-05-31
Actually, here's the master bug report ...
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492)

Been running 12 hours straight, with only gdm start problems at boot ... easily fixed with a ctrl+F2 and gdm restart cmd.  

My workaround:
removed compiz

Added to xorg.conf under Monitor0 (might not matter) ...
HorizSync    31.5-48.5
VertRefresh  59-75


 added to grub ...
video=LVDS-1:e video=VGA-1:d i915.modeset=0
 

Turned off Screen Saver and Power Management
 

 Removed the >>> Shockwave Flash <<< plugin from  Firefox 3.6.3.


firefox-bin was flooding .session-errors ... since removing flash, very  few firefox-bin errors.  I'm still getting random .xsession-errors from  polkit-gnome-authentication-agent, gnome-terminal,  firefox-bin, rhythmbox ... but 12 hours straight uptime is pretty good  compared to the immediate X startup crash.

Cheers,

Mike

---

