---
title: "upper and lower panels disappears when trying to shutdown"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by kevinh211 on 2008-06-22
I have been using Ubuntu for months without ever having a problem. But with in the last week i am unable to shut down or restart.
When I click on the green running man in the upper right panel so i can shut down my computer, both the upper and lower panels disappear. The log off/restart/shut down screen never comes up at all. All that shows is the desktop without the upper and lower panels.
I think it started when I updated Ubuntu. I noticed their is a new kernel when i started the computer. My computer is dual boot with windows, and now about 6 different kernels for Ubuntu... 2.6.22-** ... are their to many kernels, is that even possible?
What can i do to fix my problem? I have no idea where to start.
Thanks

---

### Post by iaculallad on 2008-06-22
For the Shutdown/LogOff/Restart problem:

```
gksu /usr/sbin/gdmsetup
```

For the new kernels that shows up on your GRUB boot menu, you could actually edit your /boot/grub/menu.lst file and delete/comment (by placing # before the line of word) your OLD kernel files so that only the newest Kernel boot option will show up.

```
gksu gedit /boot/grub/menu.lst
```

Note: You can also delete your OLD kernel files using the Synaptics Package Manager, search for the "linux-image" string (that's w/o quote).

---

### Post by Portable_Jim on 2008-10-08
Try running
```
df -h
```Post the output.
For me, this disk was full.
For example:
```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             3.7G  3.7G   0  100% /
```

---

