---
title: "Port the joojoo OS to joggler"
date: 2010-09-08
forum: Programming Talk
---

### Post by pipposanta on 2010-09-08
I am trying to port joojoo os [https://thejoojoo.com/](https://thejoojoo.com/) (which is based on ubuntu) to the o2 joggler. [http://yourfamily.o2.co.uk/o2familyjoggler/](http://yourfamily.o2.co.uk/o2familyjoggler/)
I have beginned creating the efi partition scheme on a usb since the joggler uses efi. see below:
-------------------------
 fat16 |      ext3      |
-------------------------
i place the joojoo os, which you can get here: [http://rapidshare.com/files/413637013/joojoo-015.zip.html](http://rapidshare.com/files/413637013/joojoo-015.zip.html) in the ext3 partition and the joggler efi boot files in the fat16 partition.

I tried to boot the joggler and the boot process start but hangs at:
```
run-init: opening console: No such file or directory
8.443250 Kernel panic - not syncing: Attempted to kill init!
8.422125 Pid: 1, comm: run-init Tainted: G C 2.6.32.2 #6
8.460931 Call Trace:
```
i don't write the call trace for comfort, they a mix of panic, do_exit, complete_and_exit, syscall_call, init_cyrix nad some numbers.

Can you help me?

Thanks in advance!

---

