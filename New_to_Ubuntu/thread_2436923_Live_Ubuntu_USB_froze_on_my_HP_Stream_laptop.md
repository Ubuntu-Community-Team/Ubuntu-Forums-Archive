---
title: "Live Ubuntu USB froze on my HP Stream laptop"
date: 2020-02-15
forum: New to Ubuntu
---

### Post by dbee on 2020-02-15
I'm trying the bootable live version of Ubuntu (latest) that i downloaded this morning.

When i booted up with the USB I connected to the network and opened firefox. But after a few seconds the system froze.

I tried doing a Ctrl+al+delete but nothing happened so i had to do a hard shutdown manually.

> 
ubuntu@ubuntu:~$ free -m 
                    total        used        free      shared  buff/cache   available
Mem:           1892         678          65         531        1147         522

I don't have 4 GB of RAM, but the underlying OS is the behometh that is windows 10 and it seems to run OK ...

Should i install ubuntu or not ? Maybe I should add more memory specifically for ubuntu ?

Processor Intel(R) Celeron(R) CPU N3060 @ 1.60GHz, 1601 Mhz, 2 Core(s), 2 Logical Processor(s)
System Model HP Stream Laptop 11-y0XX

I booted again and everything seems to be working. So i'm in two minds about the thing. Will the install be better than the live cd ?

---

### Post by ank2 on 2020-02-15
Are you familiar with the Linux command line? Then you could try CTRL+ALT+F3 to get a console, log in and check the logs in **/var/log/messages** or **/var/log/syslog** and try to figure out why the GUI froze.

If you want to try a different Linux have a look at [https://www.makeuseof.com/tag/5-best-linux-distros-installation-usb-stick/](https://www.makeuseof.com/tag/5-best-linux-distros-installation-usb-stick/)

---

### Post by dbee on 2020-02-16
Thanks Ank2,

I'm pretty sure if Ctrl+Alt+Delete doesn't work when the system freezes then Clrt+Alt+F3 isnt' going to work either :-(

Yes, I'm familiar with the command line :-)

---

### Post by guiverc on 2020-02-16
I don't see your connection with CTRL+ALT+DEL and CTRL+ALT+F3; both are keys that your hardware ignores (though firmware will reboot if it's active such as in POST), and are caught by the OS and dealt with there.  Ctrl+Alt+Fn key is usually enabled, Ctrl+Alt+Del is often disabled as SysRq keys are used far more frequently.  As Ubuntu is a Linux kernel I'd stick to Sysrq key combinations used by the linux kernel (over key combinations made popular in microsoft DOS).  

I didn't see the release or ISO of Ubuntu you are using; latest doesn't help much as some people only count LTS release, others count .04 releases, others count all, leaving off other details like .1/.2/.3/.4/.5, desktop/server etc. Being specific is helpful to us providing useful information.

Did you verify your download? ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)?](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)?) and then write to install media?  ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) where CD refers to any media used, inc. cd/dvd/hdd/ssd/thumb-drive)

I would try ctrl+alt+fn key, esp. Alt-Sysrq key combination (to at least know if GUI is frozen assuming desktop is in use) as it'll provide clues as to kernel health. Yes you could search log files for squashfs errs, but validating media before hand is far easier (if it fails on that box, I'd do the 'Check disc for defects' on another box and if it fails there too - assume it's bad!)

---

