---
title: "TIP: Creative soundcard pop/click fix for Karmic Koala."
date: 2009-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Shazaam on 2009-11-20
EDIT (update)---
Try this first...
Open your pulseaudio volume control (Sound Preferences). If (under the hardware tab) you have your device set as 4.1 (or 5.1 or 7.1) and you lack a center speaker change it so it reads 4.0 (5.0 or 7.0). Worked on Lucid and Natty and the subwoofer still works as normal.



Note: this tip MAY affect other sound cards too. :)

To fix pops/clicks (and maybe the hissing bug too) while listening to audio on Karmic Koala try this...

Open /etc/pulse/default.pa for editing (as root)-
Go to (on your panel) Applications>Accessories>Terminal and in the box that opens enter this=
```
gksudo gedit /etc/pulse/default.pa
```
Terminal will ask you for your USER password (the one you log into Ubuntu with); while you enter it you will see NO input. Don't worry, the password will be there so go ahead and hit your enter key. Gedit will open default.pa for editing.
Scroll down until you find this-
```
### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect 
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif
```
This line is the one that you want to change-
```
load-module module-udev-detect
```
Add tsched=0 (that's a zero) to the end of it so it looks like this-
```
load-module module-udev-detect tsched=0
```
I also commented out (with a # in front of the line) bluetooth support as I don't use it-
```
### Automatically load driver modules for Bluetooth hardware
#.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
#.endif
```
Then go to File-Save (upper left). When the file is saved a copy of your old version is kept with a ~ (tilde) added to the end. I would recommend renaming the backup (~) file with a different name (default.pabak) so it doesn't get deleted.
Last but not least you can either reboot or kill and restart pulseaudio.
If you have problems/bugs after this edit it is a simple matter to delete the new file and then rename the old one back to default.pa
You can do this through the terminal or by opening nautilus as root-
```
gksudo nautilus
```
(CTRL+H to show hidden files)
Just be careful running nautilus as root as any changes you make are pretty much PERMANENT!

Disclaimer:
I have NOT tried running any other audio/sound apps besides Rythmbox after performing this fix. There is a chance it might affect other parts of your audio subsystem (movies, flash, games etc). If you do encounter any problems do the file rename fix stated above.

Links...
[http://www.pulseaudio.org/wiki/Modules](http://www.pulseaudio.org/wiki/Modules)
Thanks marmuta (post #7) [http://ubuntuforums.org/showthread.php?t=1005668](http://ubuntuforums.org/showthread.php?t=1005668)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/336965](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/336965)
and...
[http://www.google.com/search?hl=en&as_q=&as_epq=tsched%3D0&as_oq=Karmic&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=&as_epq=tsched%3D0&as_oq=Karmic&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)

---

### Post by Stosskraft on 2009-11-25
I have followed this any now I have no sound at all. Ideas?

---

