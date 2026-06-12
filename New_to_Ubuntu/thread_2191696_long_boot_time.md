---
title: "long boot time"
date: 2013-12-03
forum: New to Ubuntu
---

### Post by mohitsharma3172 on 2013-12-03
My samsung laptop with i3(3rd gen) , 500 gb hdd and 1gb internal intel 3000 graphics.
It came with windows 7 but I ditched it and installed ubuntu as a standalone OS.
but it takes over a minute to boot.
But the Ubuntu OS in my college pc(dual core,250gb hdd,no graphics) boots in under 30 secs.
please help.

---

### Post by fantab on 2013-12-04
Does Grub menu show at startup?
Is 'Fastboot' enabled in BIOS?
You can also disable 'unwanted' Startup apps from 'Startup Applications'.

---

### Post by amjjawad on 2013-12-05
> **mohitsharma3172 said:**
> My samsung laptop with i3(3rd gen) , 500 gb hdd and 1gb internal intel 3000 graphics.
It came with windows 7 but I ditched it and installed ubuntu as a standalone OS.
but it takes over a minute to boot.
But the Ubuntu OS in my college pc(dual core,250gb hdd,no graphics) boots in under 30 secs.
please help.

Hi,

I fail to see any problems here. However, would you please tell us what version of Ubuntu are you using? RAM? what version of Ubuntu your College PC has? are you sure both are Ubuntu not Lubuntu or Xubuntu?

---

### Post by Impavidus on 2013-12-05
How fast is the hard drive? Booting speed is usually limited by the speed of the hard drive, so it can easily make 15s difference.

---

### Post by mohitsharma3172 on 2013-12-14
thank you for your help...
fastboot is enabled...
grub menu does not show...
actually it takes upto a minute to get to the login screen sometimes...
that is what i'm annoyed with...

---

### Post by mohitsharma3172 on 2013-12-14
my college pc and my laptop both have 4gb ram...
both are using ubuntu 13.10...

---

### Post by oldfred on 2013-12-15
Use log file viewer or look at dmesg or other log files with editor or quick list with cat.
 cat /var/log/dmesg

You want to review for long times between tasks, repeated tasks trying and then failing or suceeding and outright errors or failures to load something.

Entries like this which are my slow entries :) SSD is pretty fast, but mounting partition & swap are slowest part.

```
[    3.699713] FDC 0 is a post-1991 82077
[    5.744025] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[    6.018105] Adding 3076412k swap on /dev/sdc11.  Priority:-1 extents:1 across

```

---

