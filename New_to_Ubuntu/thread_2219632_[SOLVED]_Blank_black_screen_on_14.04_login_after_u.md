---
title: "[SOLVED] Blank black screen on 14.04 login after upgrade from 13.10"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by CelticWhisper on 2014-04-24
Turns out my remote-desktop vino-server question was premature.  I just got home and tried booting into my newly-upgraded 14.04 environment to be "greeted" with a blank black screen.  This is after the Ubuntu 14.04 "colored dots" boot screen.  I have no GRUB options menu so I can't tweak boot options by pressing "e".  Autologin carried over from 13.10 with an "htpc" user set to autolaunch XBMC.

-I can tell there's some kind of video driver working, as I'm able to press the Ctrl key and get the "sonar ping" effect to locate the cursor (or where the cursor would be if I could frelling see it)
-Ctrl+Alt+F1 shows the following:
```
Ubuntu 14.04 LTS Camineet tty1
Camineet login: * Starting Samba Auto-reload Integration             [ OK ]
* Starting automatic crash report generation                         [ OK ]
* Starting cups-browsed - Bonjour remote printer browsing daemon     [ OK ]
* Stopping Restore Sound Card State                                  [ OK ]
* Stopping Samba Auto-reload Integration                             [ OK ]
* Starting Restore Sound Card State                                  [[COLOR="#FF0000"]fail[/COLOR]]
```

I tried ```
apt-get purge "nvidia *"
```followed by ```
apt-get install nvidia-current
``` but that didn't work - still have the black screen with "ping" effect.

I'd rather not have to format and reinstall, as I have an XBMC library on this system that my whole family uses and it'd be quite irritating to have to rebuild it.


<RANT>
Also, if I may be permitted a small measure of venting, the only changes/installations I made to this system atop a bog-standard 13.10 base were
-Edited /etc/fstab to automount an external HDD (preserved by 14.04 as it was waiting for it to mount when I moved the system into my office from the living room).
-Installed ubuntu-restricted-extras.
-Installed XBMC and added it to startup items.

No manually-compiled source packages (I don't think I even had build-essential installed), no drivers that weren't offered by Hardware Drivers control panel, no hardware changes post-install.  I tried to keep it as pristine as I could.  Why has a distro upgrade hosed my system like this?  This is not simple or straightforward or intuitive or user-friendly.
</RANT>


Thank you, though - quite sincerely - for your help.

---

### Post by CelticWhisper on 2014-04-24
Fixed it!

I was reading this thread:
[http://ubuntuforums.org/showthread.php?t=2073215](http://ubuntuforums.org/showthread.php?t=2073215)

and saw the bit about the incompatible fglrx driver.  The user said they removed fglrx (which I did with Nvidia) and then rebooted, leaving it at that (which I did NOT do with Nvidia, instead having re-downloaded and reinstalled the current driver).

I performed ```
sudo apt-get purge "nvidia *"
``` again and rebooted, and I'm once again looking at my beautiful XBMC environment.

My point remains, though, about upgrades breaking systems.  Shouldn't have had to do this, but at any rate, there's the fix.

---

### Post by coldcritter64 on 2014-04-24
You've reverted the install to the open source drivers (Nouveau). They are pretty good in my opinion but are different to nvidia. I've only recently switched back to nvidia on this Debian Wheezy install, kept getting full system lockups with some video playback with Nouveau and xinerama on dual monitors. They both have their pros and cons etc. 

Bugs sometimes happen and upgrades are usually good for a few. You may be able to look at nvidia drivers down the track if you need different driver functionality later on. Cheers, coldcritter64

---

