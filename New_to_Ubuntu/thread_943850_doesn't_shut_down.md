---
title: "doesn't shut down"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by DetroitLibertyPenguin on 2008-10-10
I've recently installed Xubuntu 8.04 after liking the live CD of Ubunut and I heard that XFCE was "lighter."

Well I'm having one fairly large problem. When I shutdown the computer it never actually shuts down. It shows a few lines of text, nothing that at least appears to be an error to me, then a flash screen shows up that just says XUBUNTU with a mouse, similar to that that at the loading screen, and that is as far as it gets, it never finishes the shut down. When I eventually power it down manually I don't feel as though I'm loosing any saved information, though it seems like its running a bit slower. I have no problem using the RESTART option nor the LOG OUT option. 

How can i fix this?

---

### Post by sumguy231 on 2008-10-10
If your computer is slightly older (early 2000s and older) then you might try booting with the acpi=force kernel option to get this to work properly.

To do so, run:
```
gksu gedit /boot/grub/menu.lst
```
Find the part that looks like this:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
And append "acpi=force" (without quotes) to the last line. Don't remove the # to uncomment the line.
Save the file and reboot. See if it works. At best it will, but at worst it should have no effect.

---

### Post by DetroitLibertyPenguin on 2008-10-14
The only functionality this seems to have changed is that now it seems as though there is more text displayed before going to the splash screen. I'm not sure how to capture this information in case it is pertinent. 

One other thought did cross my mind. Is this by any chance how its "supposed" to run. Like is it supposed to shut down, show some commands, show a splash screen and when the task bar disappears you are supposed to shut down manually? Perhaps similar to the old "It is now safe to shut down your Macintosh" screen from back in the early 90s. 

Of course I'd rather be able to tell it to shut down and then leave, but if I'm expected to wait around, oh well.

---

### Post by DetroitLibertyPenguin on 2008-11-12
Re: PC will shutdown but won't power off 
I know this post is several months old. But I had similar issues, and was able to resolve it more simply. 

from terminal i entered sudo shutdown now

once this activity was created I chose the fix X option

It ran some scans, then posted a message about needing to reconfigure the x11/xconfig file and that I may loose some custom settings. 

now all is well (except the scroll buttons on my trackball don't work anymore, but if its a trade off, its a good one). Though any insight on this would be well appreciated

---

