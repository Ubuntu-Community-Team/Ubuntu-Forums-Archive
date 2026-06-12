---
title: "Stuck"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by szaqlon on 2008-07-08
I just installed XFCE. I put a splash screen that takes up the whole screen and the next time I logged out and back in it got stuck at the splash screen and it just stays there. i haven't been able to get into it since. It says "Performing Autostart..." twice at the bottom and the little circle is going like its loading, the hard drive light is even blinking but it goes no further. Is it this screen that could be causing this problem?

---

### Post by phidia on 2008-07-08
To find out if it is the image file login to a tty (Alt+Ctrl+F1) or F2-F7, and navigate to the directory that splash screen is called. Maybe it's /boot/grub/menu.lst? So cd to /boot/grub and open menu.lst with your favorite test editor. Comment out the splash screen and reboot.

---

### Post by szaqlon on 2008-07-08
That didn't do it. The splash screen I'm talking about is the one that comes up after you log in, would that be in the bootup?

---

