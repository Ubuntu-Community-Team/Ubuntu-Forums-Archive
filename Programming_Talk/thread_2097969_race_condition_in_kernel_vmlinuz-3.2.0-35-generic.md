---
title: "race condition in kernel vmlinuz-3.2.0-35-generic"
date: 2012-12-25
forum: Programming Talk
---

### Post by rnerwein on 2012-12-25
hi
i think there is a "little" race condition in the kernel (looks for me there is
a relation with "/etc/ld.so.cache or /lib/x86_64-linux-gnu/libc.so.6".
i presume it's the cache
first my configuration:
acer 4 cores - 4 GB main storage
kernel: vmlinuz-3.2.0-35-generic - the system is "totaly" up to date
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

oh i noticed that it can be reproduced with the cat command too:
cat /sys/class/hwmon/hwmon1/device/performance_level
cat /sys/class/hwmon/hwmon1/device/performance_level
produce in /var/log/syslog:
 Dec 25 12:53:28 tschang kernel: [22091.406299] [drm] nouveau 0000:03:00.0: Register 0x00004030 not found in PLL limits table
sounds dangerous 
but when you wait about 20 second between the cat commands - no message will be shown (cat returns errcode 0 ! )
cheers


for further information see the attached file with C source code.
cheers

---

### Post by Bachstelze on 2012-12-25
You should post that on the kernel mailing lists, not here....

---

### Post by rnerwein on 2012-12-25
> **Bachstelze said:**
> You should post that on the kernel mailing lists, not here....
hi
sorry - please give me a hint where i can find the kernel mailing list (that's what i thought but i find no place to post it)
cheers

---

### Post by CptPicard on 2012-12-25
Before you go bother the KML, you really should be a bit more certain in your claim that it is a kernel race condition, and to provide more context as to what you're doing in your application to make this happen. What do you base your assumptions on?

It seems like the same error message can be Googled to be found in various threads, and they seem to have something to do with the nouveau video driver.

---

### Post by rnerwein on 2012-12-26
> **CptPicard said:**
> Before you go bother the KML, you really should be a bit more certain in your claim that it is a kernel race condition, and to provide more context as to what you're doing in your application to make this happen. What do you base your assumptions on?

It seems like the same error message can be Googled to be found in various threads, and they seem to have something to do with the nouveau video driver.
hi
first why i presume it's a kernel bug - i think you know the command lsmod and lsmod is
defined: lsmod — program to show the status of modules in the Linux Kernel
and if i not on the wrong track is it a race open like a barn door ( aprox 20
second is a long time)
and about my application - as i post you can even reproduce with the "cat" command.
i guess it's probably helpful for a devolper to reproduce the bug very easy ( i was always happy when i had such a problem on my desk).
oh yes now i had a look in the internet about that problem - looks very old ( my opinion is that the problem was fixed a couple of times but the hardware is getting faster fast then the software development ( i know what PLL is).
yeah cat is a very complex application !
cheers

---

