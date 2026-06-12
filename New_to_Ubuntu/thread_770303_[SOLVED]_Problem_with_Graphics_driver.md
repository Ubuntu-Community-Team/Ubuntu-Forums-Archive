---
title: "[SOLVED] Problem with Graphics driver"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by kestrel1 on 2008-04-27
This is sort of related to my previous post: [http://ubuntuforums.org/showthread.php?t=766846&page=1](http://ubuntuforums.org/showthread.php?t=766846&page=1)
Anyway, after installing the restricted Nvidia driver on my system everything seemed OK. I then went into the Nvidia X server settings & made sure the screen resolution was set correctly. After exiting the Nvidia settings screen I went on the Internet using Firefox. I went to close Firefox using the 'x' in the top right of the screen, but noticed that the title bar was missing. I checked settings & nothing made a difference. I thought I had done something silly, so left it. I went to use the terminal & the window that opens was completely white, no title bar, menu bar or prompt text. The only way to exit this was to type 'exit' blind, as I could see no text. I opened another program & I had the same problem as I did with Firefox. I then had a think & removed the restricted Nvidia driver. Rebooted & all the previous problems with the programs disappeared. Just to check my theory I reinstalled the restricted driver & used the Nvidia settings again. Everything happened as before, no title bar etc.
Does anyone know if this is a known problem or a new one.
I will not use the restricted driver until I know of a solution.
Thanks.

---

### Post by kestrel1 on 2008-04-27
Anyone?

---

### Post by Ub1476 on 2008-04-27
You have add the following option to the device section in xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

Browse down to section "Device" (around line 30-40 probably).

And add:

```
 Option  "AddARGBGLXVisuals"  "True" 
```

Taken from [Compiz-Fusion wiki]("http://wiki.compiz-fusion.org/Hardware/NVIDIA"):)

You have to reboot.

---

### Post by Tux.Ice on 2008-04-27
yes it is defiantly a problem with compiz.

---

### Post by kestrel1 on 2008-04-27
Thanks ub1476. Used the option you mention & this sorted the problem, also had a look through the link you gave to see if anything else was required. Couldn't see anything, but all seems good now.
Thanks again.

---

