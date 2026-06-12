---
title: "initramfs problem from a fresh install"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by herbert tamayo on 2012-04-30
hi, I'm trying to install lubuntu 10.04 from my usb, i know that the iso is ok (I've already tried it from a virtual machine and it works). So I've used unetbootin to put the iso in  my usb pendrive, but when I try to boot in the target pc I got inside a console with the prompt in:

[HTML]
<initramfs>
[/HTML]

so, checking in google i found several advices but for live CDs - modifying the menu.lst of grub- but I think that it is not my case. so my question is:

what should I do to correct this error and get in the installation process?

regards

---

### Post by strask on 2012-04-30
Basically, you drop to the initramfs prompt any time the system fails to boot prior to the point where the root filesystem is mounted. There could be several, completely unrelated, reasons for this so we need more information to solve your problem.

What kind of error messages do you get just above the initramfs prompt? If you could take a photograph or something that would be awesome, or just type in as much as you can bear starting with the last messages first.

---

### Post by herbert tamayo on 2012-04-30
So, checking again and again the installation process I found something, here it is the scenario

- iso file: lubuntu 11.10-desktop-i386
-unetbootin used by put the iso in my usb
-booting from my usb i cant get the unetbootin menu, I choose the default option
-starting the ubnkern, then the ubninit
-.then I get into the <initramfs> console

errors displayed checked in the f7 tty:
```

mount: can't read 'etc/fstab' no such file or directory
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory

target filesystem doesn't have requested /sbin/init

No init found. Try passing init=bootarg.


```

that's it, it seems to add some params to the init file right?

so, my new question is:
how can I do that?
what params should I pass?

regards

---

