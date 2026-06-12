---
title: "Help to understand Kernel update choices"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by ubermadscientist on 2012-01-20
Hi;
I just installed Ubuntu 10.10, I have not yet made any changes to the updates options, repositories or software options that are default with the installation.

After doing updates yesterday and a full day of use there are more updates available and it's showing a lot of choices for the kernel.

I'm wondering if someone can assist me with understanding the difference(s) between the different kernel choices so I don't mess it up.

Here are the options offered for updates:

[LIST]
[*]Complete generic Linux kernel
[*]Header files related to Linux kernel version 2.6.35
[*]Linux kernel headers for version 2.6.35 on x86/x86_64
[*]Gereric Linux kernel headers
[*]Linux kernel image for version 2.6.35 on x86/x86_64
[*]Generic Linux kernel image
[*]Linux kernel headers for development
[/LIST]

Thanks for any assistance and/or advice.

---

### Post by snowpine on 2012-01-20
These are updates to packages that are already installed on your computer. It is normal and safe to say yes to all of the suggested updates. If you are not happy with the updated kernel, then you can choose the old one from your GRUB boot menu and troubleshoot from there.

The kernel is the core of the Linux operating system. The "image" is the actual kernel and the "headers" are used for development/compiling. There are several related files, some  of what you see are just "metapackages" that install other packages. ;) If you find the kernel fascinating then there's so much good reading material out there, for example: [http://kernelnewbies.org/FAQ](http://kernelnewbies.org/FAQ) 

It gets complicated quickly, though! And it's not something the average user needs to worry about (unless you are interested in it for a hobby/career).

---

### Post by ubermadscientist on 2012-01-20
Thank you for the quick and informative reply.

I'll check out the link - I love learning new info.

Cheers.

---

