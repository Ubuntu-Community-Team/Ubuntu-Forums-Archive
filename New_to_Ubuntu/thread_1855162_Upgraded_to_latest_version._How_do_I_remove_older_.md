---
title: "Upgraded to latest version. How do I remove older kernels."
date: 2011-10-05
forum: New to Ubuntu
---

### Post by dep0 on 2011-10-05
hi! i have succesfully upgraded to ubuntu 11.04 but i still have the old kernels installed on my computer. i would like to know what do i have to do to delete them. Thanks! 
PS : I am noobie so please answer simple.

---

### Post by cryptotheslow on 2011-10-05
I usually just remove them using Synaptic.

This how-to should still be valid for v11.04:
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by howefield on 2011-10-05
Posts spliced off to own thread :)

---

### Post by wildmanne39 on 2011-10-05
Hi, it is easier for some to use synaptic and it is a good idea to keep at least the recovery kernel, memory, and one old kernel just in case you get an update that breaks the latest kernel.
Thank you

---

### Post by proxy.qtz on 2011-10-06
You can remove them using the computer janitor utility, or you can use Synaptic, although I suggest you keep the newest kernel, and the kernel just previous to that one.

---

### Post by bspymaster on 2011-10-06
I usually keep the last two and the current one, just in case...

---

### Post by proxy.qtz on 2011-10-06
> **bspymaster said:**
> I usually keep the last two and the current one, just in case...
Nice job saying exactly what I just said, except not even answering the OP's question.

---

### Post by philinux on 2011-10-06
> **dep0 said:**
> hi! i have succesfully upgraded to ubuntu 11.04 but i still have the old kernels installed on my computer. i would like to know what do i have to do to delete them. Thanks! 
PS : I am noobie so please answer simple.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Open a terminal and cut and paste the one liner in section 5. The first one is a dry run.

The second command actually does the business.

If that is too much for you please follow some of the other gui methods suggested above.

---

### Post by VanR on 2011-10-06
I find it easier to use ubuntu-tweak to remove them.

---

### Post by mörgæs on 2011-10-06
They take up very little space. Afterwards you will probably not be able to notice that you have a few free bytes.

---

### Post by CharlesA on 2011-10-06
> **mörgæs said:**
> They take up very little space. Afterwards you will probably not be able to notice that you have a few free bytes.
This.

If you really want to remove them, you can run this:

```
#!/bin/bash

### rmkernel.sh
### Purges all but the two most recent kernels
### Based on original command found here:
### http://ubuntuforums.org/showthread.php?t=1658648
### Modified by Charles Auer to keep the two most recent kernels
### Tested 2/27/2011

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1 | xargs apt-get purge --assume-yes
# eof
```

---

### Post by dep0 on 2011-10-22
> **philinux said:**
> [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Open a terminal and cut and paste the one liner in section 5. The first one is a dry run.

The second command actually does the business.

If that is too much for you please follow some of the other gui methods suggested above.

Thanks a lot. That worked out fine.

---

### Post by sachakagan on 2011-11-22
Am reacting to an earlier post in this thread: How can you write that old Kernels take up little space? Old Kernels take up a lot of space! I just freed up about 800 MB by removing them today on my system (10.10)...

---

### Post by CharlesA on 2011-11-22
> **sachakagan said:**
> Am reacting to an earlier post in this thread: How can you write that old Kernels take up little space? Old Kernels take up a lot of space! I just freed up about 800 MB by removing them today on my system (10.10)...

Unless you want to compile your own (which might be more pain then it's worth), just keep removing the old kernels to free up space.

---

### Post by mörgæs on 2011-11-22
> **sachakagan said:**
> Am reacting to an earlier post in this thread: How can you write that old Kernels take up little space? Old Kernels take up a lot of space! I just freed up about 800 MB by removing them today on my system (10.10)...

That means you had a lot of them :-) I would guess that a 10.10 kernel is about 80 MB of size.

---

### Post by CharlesA on 2011-11-22
> **mörgæs said:**
> That means you had a lot of them :-) I would guess that a 10.10 kernel is about 80 MB of size.

Aye.

I checked /boot on my Lucid server and each kernel was around 8MB.

```
charles@Thor:~$ ls -lh /boot
total 77M
-rw-r--r-- 1 root root 632K 2011-09-13 17:00 abi-2.6.32-34-server
-rw-r--r-- 1 root root 632K 2011-10-11 10:10 abi-2.6.32-35-server
-rw-r--r-- 1 root root 109K 2011-09-13 17:00 config-2.6.32-34-server
-rw-r--r-- 1 root root 109K 2011-10-11 10:10 config-2.6.32-35-server
drwxr-xr-x 3 root root 4.0K 2011-11-09 10:36 grub
-rw-r--r-- 1 root root 7.9M 2011-03-22 15:51 initrd.img-2.6.32-30-server.rr26xx
-rw-r--r-- 1 root root 7.9M 2011-04-21 19:39 initrd.img-2.6.32-31-server.rr26xx
-rw-r--r-- 1 root root 7.9M 2011-05-30 06:40 initrd.img-2.6.32-32-server.rr26xx
-rw-r--r-- 1 root root 7.9M 2011-07-15 06:33 initrd.img-2.6.32-33-server.rr26xx
-rw-r--r-- 1 root root 8.1M 2011-09-29 07:16 initrd.img-2.6.32-34-server
-rw-r--r-- 1 root root 7.9M 2011-09-29 06:41 initrd.img-2.6.32-34-server.rr26xx
-rw-r--r-- 1 root root 8.1M 2011-11-08 07:06 initrd.img-2.6.32-35-server
-rw-r--r-- 1 root root 7.9M 2011-11-08 06:58 initrd.img-2.6.32-35-server.rr26xx
-rw-r--r-- 1 root root 157K 2010-03-23 02:40 memtest86+.bin
-rw-r--r-- 1 root root 2.1M 2011-09-13 17:00 System.map-2.6.32-34-server
-rw-r--r-- 1 root root 2.1M 2011-10-11 10:10 System.map-2.6.32-35-server
-rw-r--r-- 1 root root 1.4K 2011-09-13 17:03 vmcoreinfo-2.6.32-34-server
-rw-r--r-- 1 root root 1.4K 2011-10-11 10:11 vmcoreinfo-2.6.32-35-server
-rw-r--r-- 1 root root 4.0M 2011-09-13 17:00 vmlinuz-2.6.32-34-server
-rw-r--r-- 1 root root 4.0M 2011-10-11 10:10 vmlinuz-2.6.32-35-server

```

Must have had a ton of them to add up to 800MB, unless you removed them via apt-get, which would free up around 200MB per kernel, since that would remove the headers too.

---

