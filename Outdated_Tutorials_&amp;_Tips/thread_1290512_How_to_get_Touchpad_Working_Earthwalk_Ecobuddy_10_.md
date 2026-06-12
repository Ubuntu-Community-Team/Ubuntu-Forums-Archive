---
title: "How to get Touchpad Working Earthwalk Ecobuddy 10 series"
date: 2009-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by gali98 on 2009-10-13
Hello all!
    I searched the web and could find this info no where, So I finally emailed earthwalk and got a fix.
    The earthwalk ecobuddy works great with ubuntu except for the touchpad which doesn't respond at all on install.

The remedy is very simple (though kinda off the wall.)
Simply open up the grub menu.lst

```
sudo gedit /boot/grub/menu.lst
```

and find the line line that says

```
# defoptions=quiet splash
```
and add 
```
i8042.nomux
```
so that it says 
```
# defoptions=quiet splash i8042.nomux
```

Then save and exit and run
```
sudo update-grub
```

Then reboot and the touchpad works!
I'm not sure of the exact config you would do for grub2 (karmic), but I am sure it is similar.
Kory

---

### Post by ibuclaw on 2009-11-05
Thanks for the tip gali98. :)

For Grub2, you'll edit:
```
/etc/default/grub
```
And then change:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux"
```
Then run the same as the above:
```
sudo update-grub
```

Regards
Iain

---

