---
title: "[SOLVED] Elongated pictures/font - Adjustment possible"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by AlexOslo on 2008-11-28
I installed Ubuntu 8.04 on my Dell Gx270 with a Dell flatscreen. Picture looked fine using other OS's, but with this one pictures and font are somewhat elongated.

Anyone know of a fix for this?

Alex

---

### Post by a0u on 2008-11-28
If it's simply a matter of screen resolution, you can edit Xorg.conf or use xrandr:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I notice you are using 8.04.  Sometimes upgrading (to 8.10) will solve some driver problems.

---

### Post by AlexOslo on 2008-11-28
> **a0u said:**
> If it's simply a matter of screen resolution, you can edit Xorg.conf or use xrandr:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I notice you are using 8.04.  Sometimes upgrading (to 8.10) will solve some driver problems.

Thank you for that helpful site! 

I checked the screens recommended resolution (with screen buttons), which was 1280x1024 85 hz, and wrote in a terminal:

 $ xrandr --output VGA-0 --mode 1280x1024 --rate 85

I'll know if it worked at the next boot, then!

Alex

---

### Post by AlexOslo on 2008-11-29
> **AlexOslo said:**
> Thank you for that helpful site! 

I checked the screens recommended resolution (with screen buttons), which was 1280x1024 85 hz, and wrote in a terminal:

 $ xrandr --output VGA-0 --mode 1280x1024 --rate 85

I'll know if it worked at the next boot, then!

Alex

Unfortunately this didn't work. Picture looks the same.
I am having trouble knowing what to do with the instruction page I was recommended,
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
since the above didn't work. It says

> Setting xrandr commands in .xprofile

A user's ~/.xprofile file is executed on Xorg startup if it exists and is executable. You can copy and paste xrandr command line strings into this file so they're executed when you log in. For example:

  $ xrandr --output VGA-0 --mode 800x600

The line "copy and paste xrandr command line strings into this file (above)" doesn't tell me much. Does anyone know how to locate this "~/.xprofile file"?

Alex

---

### Post by AlexOslo on 2008-12-17
Problem was posted under a different heading here, and got solved:

[http://ubuntuforums.org/showthread.php?t=1003490](http://ubuntuforums.org/showthread.php?t=1003490)

---

