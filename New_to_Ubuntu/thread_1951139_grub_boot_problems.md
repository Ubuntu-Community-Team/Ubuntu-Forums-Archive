---
title: "grub boot problems"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by rpatmullin on 2012-04-02
I created /etc/grub.d/66_custom and added my menuentries for grub boot menu. Set permissions so that only 00_header and 66_custom have execute permissions.  Have carefully checked syntax. Now boot takes me to grub prompt.  I can set root and boot sys, but cannot figure out what I did wrong.  Any help?

Running kubuntu 11.10 on /dev/sda1   and server 10.10 on /dev/sda2

Thanks

---

### Post by Mark Phelps on 2012-04-02
Why did you mess with the perms on the other boot files?  Just set them ALL back to the proper perms and, hopefully, you will be booting OK again.

Whenever you're messing around with system stuff like this, it's always best to change only ONE thing at a time.

---

### Post by oldfred on 2012-04-02
I found this in my notes:

From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

I have a grub install in a flash drive and just manually maintain the grub.cfg since there is no system install with scripts.

---

