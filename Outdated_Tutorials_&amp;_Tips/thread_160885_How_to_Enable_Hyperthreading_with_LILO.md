---
title: "How to Enable Hyperthreading with LILO"
date: 2006-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by deanjm1963 on 2006-04-15
Hyperthreading is built into the kernel, it's just not enabled. I had noticed on another thread how to enable hyperthreading for GRUB users, so I played around, did a little reading, trial and error, and here it is for LILO users.

Older Intel processors such as mine, 3.06ghz with HT are single core, so use Linux-686.

Newer Intel processors with Dual Core and HT, use Linux-686-smp

There's a big difference between having "2 threads being abled to run concurrently" and having "2 processors or cores".

Some distros, such as my-ex Mandriva installed an SMP kernel by default. It worked for that distro, but Ubuntu is a little different. I tried several times using the Linux-686-smp, it would run, but I would end up with HAL errors.

I use XFS for my file system so hence I have LILO installed instead of GRUB.

To enable hyperthreading when you're using LILO, do the following.

in a terminal

**sudo gedit /etc/lilo.conf**

look for

**# append=""**

change that to

**append="ht=on"**

save lilo.conf

then run **sudo lilo** and reboot

hyperthreading in now enabled for LILO users

You won't notice a super improvement, but things will be "snappier" and a "little faster". Remember, Hyperthreading is NOT 2 cores/processors, it allows multiple threads to be run concurrently. Some operating systems see it as two processors (smp), such as XP, Mandriva, Fedora, but Ubuntu (Debian) sees it as one and needs to be enabled as a kernel command line option.

Hope this helps.

---

### Post by tseliot on 2006-04-23
Guide added to the USDF!
[http://doc.gwos.org/index.php/Enable_Hyperthreading_with_LILO]("http://doc.gwos.org/index.php/Enable_Hyperthreading_with_LILO")

---

