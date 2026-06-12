---
title: "Intrepid doesn't read Graphics card"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Michl on 2008-11-13
I upgraded to Intrepid from Heron on a Dell C610 and
now I hae a mess.  I only get a command line.

I've had Ubuntu since 6.10 and never had such a
problem with an upgrade.

M

---

### Post by kansasnoob on 2008-11-13
Since you can get to terminal run:

```
sudo dpkg-reconfigure xserver-xorg
```

Maybe that'll get it done. Occasionally something doesn't work right during the installation.

---

### Post by Tak11 on 2008-11-13
> **Michl said:**
> I upgraded to Intrepid from Heron on a Dell C610 and
now I hae a mess.  I only get a command line.

I've had Ubuntu since 6.10 and never had such a
problem with an upgrade.

M

if your in the command line, try typeing startx, if it tells you to do something *ie install a package* just follow the directions, get us the output,

---

### Post by kansasnoob on 2008-11-13
Super-duper excellent thread:

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by Michl on 2008-11-13
> **kansasnoob said:**
> Super-duper excellent thread:

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

The thread begins with this:
UPDATE: This method does not work with Hardy Heron and probably all versions to follow (including Intrepid Ibex). This method seems to ONLY work with Gutsy Gibbon and older.
I think this is because the newer versions of xserver-xorg rely more on auto-detecting the configuration during runtime rather than looking at xorg.conf.
/UPDATE

---

### Post by Michl on 2008-11-13
> **kansasnoob said:**
> Since you can get to terminal run:

```
sudo dpkg-reconfigure xserver-xorg
```
Maybe that'll get it done. Occasionally something doesn't work right during the installation.

Unfortunately this didn;'t work.

---

