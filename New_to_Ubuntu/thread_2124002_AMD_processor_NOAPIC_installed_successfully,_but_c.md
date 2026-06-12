---
title: "AMD processor NOAPIC installed successfully, but cannot boot"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by algander on 2013-03-09
Hello, 
i have an HP DV5-1115el with an AMD Turion ZM-84 64x2 processor.
on which i had already installed in the past ubuntu 10 on this laptop without any issues. 
i've recently formatted it and decided to pass on Ubuntu 12.04 from scratch, at first i had this error when booting from CD:
 [FONT=Ubuntu Mono]Kernel panic - not syncing: Fatal Machine Check on current CPU
[/FONT]I quickly solved passing the noapic, acpi=off parameters that i found described in many posts.

It worked flawlessly throught the complete installation until i had to remove the CD and reboot.
[FONT=Ubuntu Mono]
[/FONT]When i try to boot now from the main HDD i receive the same kernel panic and errors i had before even if i input the same parameters i gave when installing from CD.
[FONT=Ubuntu Mono]
note: im somewhat slightly less than an Ubuntu beginner so i may do wrong on any passage





ps:  the full length log is always the same if i give parameters or not

```

[         1.172071] [Hardware Error] : CPU 1: Machine Check Exception : 4 Bank 0: b669c00000000135

```[/FONT]```
[FONT=Ubuntu Mono][         1.172120] [Hardware Error]: TSC 3ba44a59ea ADDR 373c1ab8
[/FONT][FONT=Ubuntu Mono][         1.172243] [Hardware Error]: Processor 2:200f31 TIME 1362852770 SOCKET 0 APIC 1 microcode 2000057
[/FONT][FONT=Ubuntu Mono][         1.172291] [Hardware Error]: Run the abocve through 'mcelog --ascii'[/FONT][FONT=Ubuntu Mono]
[/FONT][FONT=Ubuntu Mono][         1.172343] [Hardware Error]: Machine check: invalid
[/FONT][FONT=Ubuntu Mono][         1.172386] [Hardware Error]: Kernel panic - notsyncing: Fatal machine check on current CPU[/FONT][FONT=Ubuntu Mono]
[/FONT]
```[FONT=Ubuntu Mono]

[/FONT]

---

### Post by algander on 2013-03-13
also trying other linux distribuitions did not helped at all, is the cpu damaged at the point to be unusable on linux? possible?

---

### Post by grahammechanical on 2013-03-13
This might be of interest if not of much help

[http://en.wikipedia.org/wiki/Machine_Check_Exception](http://en.wikipedia.org/wiki/Machine_Check_Exception)

Regards.

---

### Post by squakie on 2013-03-13
if noapic and acpi=no were added to get the CD to boot, you will need to add those in order to boot the installed Ubuntu as well.  force the menu at startup, edit the boot entry and continue on with the boot - that should at least boot your installation.  once booted you'll need to change/add entries in the files in /etc/default and/or /etc/grub.d

---

### Post by squakie on 2013-03-13
sorry - guess I missed that bit of trying the same options on boot of your install - sorry about that.  I was going to edit my post but I'm using android right now and haven't figured out that simple thing yet ;)

---

