---
title: "[all variants] HowTo 3D on old ATI Radeon video cards on Hardy"
date: 2008-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2008-08-14
I discovered that my pretty good but old ATI Radeon video card is not supported anymore by ATI and is not compatible with proprietary driver present in Ubuntu repositories.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

[LIST=1]
[*]Direct ATI drivers are not compatible with Xorg installed on  Hardy
[*]Fglrx driver present on the repos is not working
[*]Envyng does not recognize my video card
[/LIST]
Doing an:
```
lspci
```
I got my card brand/model
```
ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
```

And so doing an:
```
glxinfo |grep rendering
```
I get:
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

This means that on my card the 3D is not working/enabled and is not possible to use compiz-fusion or using GL applications I get slow/flickering behaviour. Well, quite horrible.

But it is possible to manage this incompatibility in this way.
Remove proprietary drivers:
```
sudo apt-get remove xorg-driver-fglrx
```
Then we need to disable the module of fglrx, editing this file:
```
sudo nano /etc/default/linux-restricted-modules-common
```
Change the entry:
```
DISABLED_MODULES=""
```
To:
```
DISABLED_MODULES="fglrx"
```
Save and exit

Now we have to install the opensource driver for ATI:
```
sudo apt-get install xserver-xorg-video-ati
```
Good. Just reboot the machine.

Now when you doing:
```
glxinfo |grep rendering
```
You'll get:
```
direct rendering: Yes
```
Good. Your (old) ATI Radeon is full 3D capable.

---

### Post by Rocket2DMn on 2008-08-14
I believe the open source ati drivers are re-enabled by default once fglrx is gone.  In Hardy, Compiz Fusion isn't allowed on cards using these drivers, so I have a workaround here for those interested - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
Also see [uhelp]community/RadeonDriver[/uhelp]
Thanks for posting this dentaku.

---

