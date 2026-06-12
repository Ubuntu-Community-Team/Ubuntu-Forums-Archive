---
title: "ctrl-alt-f1 not taking me to commandline..."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by wardrich on 2008-10-22
Having some odd issues with X... Shouldn't ctrl-alt-F1 take me to the commandline, and ctrl-alt-f7 take me to another X server window?  Right now everything but F6 throws me a black screen... and never progresses.

Not even sure where to look to figure this one out.:confused:

--edit
I think I put this in the wrong forum...

---

### Post by taseedorf on 2008-10-22
yeah man, try looking in keyboard shortcuts i believe, or keyboard...in system preferences and set the shortcuts...

---

### Post by Hexagoon on 2008-10-22
Guess you are on 8.10 beta?

---

### Post by wardrich on 2008-10-22
> **Hexagoon said:**
> Guess you are on 8.10 beta?

Sorry, I forgot to mention, I'm using 7.1, and I'm using Compiz, and a Radeon Mobility x1400.  I've got the fglrx drivers on here.

> **taseedorf said:**
> yeah man, try looking in keyboard shortcuts i believe, or keyboard...in system preferences and set the shortcuts...

Those are just for gnome shortcuts.

---

### Post by Big_Kahunaca on 2008-10-22
What do you have set for your framebuffer on the kernel line in the GRUB menu.lst

After upgrading to Intrepid I had to remove the "vga=###" part of the line because I'd just get a black screen when I dropped down to a terminal.

---

### Post by wardrich on 2008-10-22
> **Big_Kahunaca said:**
> What do you have set for your framebuffer on the kernel line in the GRUB menu.lst

After upgrading to Intrepid I had to remove the "vga=###" part of the line because I'd just get a black screen when I dropped down to a terminal.

I don't have any vga=### in my menu.lst

---

### Post by vanadium on 2008-10-22
> 7.10, and I'm using Compiz, and a Radeon Mobility x1400
Disable desktop effects and try again. I started using desktop effects with an ATI video card only one week ago on the latest Ubuntu Hardy version.

If disabling desktop effects does not resolve the issue, try whether it is solved disabling the fglrx drivers.

Anyway, I strongly recommend you to upgrade to (super stable long term supported) Hardy release. For me, Ubuntu 7.10 was the worst version I have known with serious issues related to my graphics. Things have vastly improved in 8.4 (Hardy) for me: I can even hibernate and suspend without problem now (and yes, I finally switched to compiz-fusion (desktop effects)).

---

### Post by overdrank on 2008-10-22
> **wardrich said:**
> Sorry, I forgot to mention, I'm using 7.1, and I'm using Compiz, and a Radeon Mobility x1400.  I've got the fglrx drivers on here.



Those are just for gnome shortcuts.

Hi and I did recall some issues with the Virtual Terminals with 7.10 and this link may help
[http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825)

---

### Post by wardrich on 2008-10-22
> **vanadium said:**
> Disable desktop effects and try again. I started using desktop effects with an ATI video card only one week ago on the latest Ubuntu Hardy version.

If disabling desktop effects does not resolve the issue, try whether it is solved disabling the fglrx drivers.

Anyway, I strongly recommend you to upgrade to (super stable long term supported) Hardy release. For me, Ubuntu 7.10 was the worst version I have known with serious issues related to my graphics. Things have vastly improved in 8.4 (Hardy) for me: I can even hibernate and suspend without problem now (and yes, I finally switched to compiz-fusion (desktop effects)).


I think I'll let the update manager run while I'm in bed, the lack of an update has mostly been due to lack of time... and also lack of a good memory :P

8.04LTS = Hardy, right?

---

### Post by sazan on 2008-10-22
> **taseedorf said:**
> yeah man, try looking in keyboard shortcuts i believe, or keyboard...in system preferences and set the shortcuts...

i have seen the same problem at my fren's system .. but in a different distro than ubuntu..

---

### Post by AndyCooll on 2008-10-22
> **wardrich said:**
> 8.04LTS = Hardy, right?
Correct!
:cool:

---

### Post by wardrich on 2008-10-22
Sweet, did the upgrade but it didn't help.  I'll refer to that thread that was posted a while back.

Found the fix in a link:

```
sudo modprobe vga16fb
sudo modprobe fbcon
```

---

