---
title: "[SOLVED] How to fix my xserver from Ubuntu Cdrom?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by LastWho on 2008-11-28
Hi,
i got my xserver broken somehow, and i ve to fix it to knight but i don't ve an internet connection, so i dlike to know if it possible to fix it directly from cdrom, and how plz?!

thx

---

### Post by w4ett on 2008-11-28
It's pretty easy to do right from the regular installation....at boot press the "ESC" key which will take you to the grub menu.  Select recovery, and from the menu, then select "xfix".  This might just to the trick.

---

### Post by LastWho on 2008-11-28
thx w4ett, so there is no need to do any "sudo" things :p

---

### Post by davidbilla on 2008-11-28
> **LastWho said:**
> Hi,
i got my xserver broken somehow, and i ve to fix it to knight but i don't ve an internet connection, so i dlike to know if it possible to fix it directly from cdrom, and how plz?!

thx

If you want to revert back to the default settings, just replace the contents of your machine's '/etc/X11' with the '/etc/X11' from the cd-rom. Type the following (with the appropriate changes), after booting from the cd-rom.

```
cp /etc/X11/* /media/<your-disk-root-partition>/etc/X11/
```

I am assuming your hard disks are mounted in /media. Make the necessary changes. This method has always worked for me. Breaking the display and replacing /etc/X11/ using the cd-rom is something I do as often as at least once in a month! (I'm trying to fix OpenGL in one of my systems, and I always end up breaking the xserver if I tried long enough!)

I hope this works for you. Normally I don't think I see any reason that this won't work. But this is just my experience anyway. If you're game, just try it out. If you still have qualms about it, just make a backup of your current /etc/X11 and try the above method. It should work. Let me know.

---

### Post by w4ett on 2008-11-28
> **LastWho said:**
> thx w4ett, so there is no need to do any "sudo" things :p

That's right.....however, in the old days of 7.04.  (Yuk Yuk) the command was:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This command still works, BTW

---

