---
title: "how is /proc mounted by default?"
date: 2020-05-16
forum: New to Ubuntu
---

### Post by apla on 2020-05-16
I want to change my mount configuration for /proc to use hidepid and a specified gid mount option.
I guess I could just write that in fstab and be done with it.

However I wondered: [I]who mounted /proc in the first place, with what exact options?
[/I]
There appears to be no systemd mount unit responsible.
The "with what exact options" bit pertains to that **mount** does not include default options.

I could not find any information on this, although it might just be that I'm bad at searching.
Best Wishes

---

### Post by Impavidus on 2020-05-16
What Ubuntu is this? There's no /dev/proc in my Xubuntu 19.10.

---

### Post by apla on 2020-05-16
Good point, I was confused and talking about /proc. Been reading a lot about pseudo-devicefiles and must have unconsciously warped proc to be a pseudo-device in my head, because folks tend to refer to it as a pseudo-filesystem.

That also explains why I had a hard time finding information on it. According to the man page it is usually "mounted by the system", I figure that means the kernel. Thanks for your help!

---

### Post by QIII on 2020-05-16
/proc is a virtual file system, or a pseudo-file system that doesn't contain any real files, but is maintained by the kernel to provide information about run-time information like memory used, processor information, etc.

If you were to look at /proc, you'd see that with a few exceptions all the file sizes are 0.  You can use the command line to get instantaneous information from some of the "files" in /proc, like:

```
 xxxx@xxxx:~$ uptime
 12:40:03 up 179 days, 12:39,  1 user,  load average: 0.00, 0.01, 0.05

```

---

### Post by apla on 2020-05-16
This answer hardly relates to my question. In fact, for the question of *who mounted it* it is fully irrelevant - both, devices and file systems, are mounted at some point by someone or something.

---

### Post by QIII on 2020-05-16
It is entirely relevant.  It is maintained by the kernel at runtime.  That is "who mounted it", as you suggested.

Your query may have been solved as far as your concerns, but others might read this thread and not have any idea what you learned in your research.

---

### Post by Holger_Gehrke on 2020-05-16
Actually /proc, /sys/, /run, /dev, /tmp and some others are mounted by systemd very early in the boot process. See [https://www.freedesktop.org/wiki/Software/systemd/APIFileSystems/](https://www.freedesktop.org/wiki/Software/systemd/APIFileSystems/) for details. You can change mount options for these by putting lines for them in /etc/fstab, /lib/systemd/system/systemd-remount-fs.service will then remount them with these option.

Holger

---

