---
title: "Install with ACPI workaround - is my PC not compatible?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-06-17
What does it mean when you install with ACPI workaround. This was the only way I could get Kubuntu installed on my machine. In fact it is not a proper install...everything has to start from scratch again when I close down. Does this mean that my PC is not compatible with Ubuntu/Kubuntu

---

### Post by spiderbatdad on 2008-06-17
I am assuming you used F6 from the install options screen and added acpi=off to the end of the boot line.

To make this change permanent, after install, you need to edit the file /boot/grub/menu.lst as administrator, with the command: ```
gksu gedit /boot/grub/menu.lst
``` Scroll down to this section:
```
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=####'S ro acpi=off
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

make it look like the example above, by removing quiet splash and adding acpi=off. The line just above the section may say, "Savedefault=false.  Change that to true.

---

### Post by dunbrokin on 2008-06-17
> **spiderbatdad said:**
> I am assuming you used F6 from the install options screen and added acpi=off to the end of the boot line.

To make this change permanent, after install, you need to edit the file /boot/grub/menu.lst as administrator, with the command: ```
gksu gedit /boot/grub/menu.lst
``` Scroll do to this section:
```
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=####'S ro acpi=off
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```



Thanks for that....I will try...but the (partial) install I get is very shimmery and ghost like in appearance and not very stable...will the lines you have suggested above change that. Attached is the Syslog.
make it look like the example above, by removing quiet splash and adding acpi=off. The line just above the section may say, "Savedefualt=false.  Change that to true.

---

### Post by spiderbatdad on 2008-06-17
k. I see from syslog you have edited the boot line to read acpi=off noapic nolapic. This may be overkill. You may need local apic...you might want to try acpi=off lapic, or just acpi=off....takes a little experimenting.

Also looks like something is wrong in your partition scheme...created a reiserfs partition for /var? It may be full. IDK there are a lot of errors in the syslog...like this:

 ```
 >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Jun 17 22:45:18 ubuntu kernel: [  297.509205] attempt to access beyond end of device
Jun 17 22:45:18 ubuntu kernel: [  297.509211] sda2: rw=0, want=18, limit=2
Jun 17 22:45:18 ubuntu kernel: [  297.514514] attempt to access beyond end of device
Jun 17 22:45:18 ubuntu kernel: [  297.514523] sda2: rw=0, want=3, limit=2
Jun 17 22:45:18 ubuntu kernel: [  297.515493] hfs: can't find a HFS filesystem on dev sda2.
Jun 17 22:45:18 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jun 17 22:45:18 ubuntu kernel: [  212.618295] cramfs: wrong magic
Jun 17 22:45:18 ubuntu kernel: [  212.628730] VFS: Can't find ext3 filesystem on dev sda5.
Jun 17 22:45:18 ubuntu kernel: [  212.633037] ReiserFS: sda5: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda5


```

I can't really tell if the partitioning scheme is bad or just the parameters you have tried to boot with...also looks like you have two other OSes? Fat and another linux distro?

Anyway ubiquity failed (so your installation is not good) with the above parameters,,,and possibly the above partition scheme. If you are manually partitioning, make sure you specify ext3 for the / (root) partition and he swap. reiserfs is ok for /var. You can always go with a default plan and move partitions later. Try acpi=off or noapic...not all three (acpi=off noapic nolapic) or acpi=off lapic.

good luck.

---

### Post by dunbrokin on 2008-06-17
> **spiderbatdad said:**
> k. I see from syslog you have edited the boot line to read acpi=off noapic nolapic. This may be overkill. You may need local apic...you might want to try acpi=off lapic, or just acpi=off....takes a little experimenting.

Also looks like something is wrong in your partition scheme...created a reiserfs partition for /var? It may be full. IDK there are a lot of errors in the syslog...like this:

 ```
 >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Jun 17 22:45:18 ubuntu kernel: [  297.509205] attempt to access beyond end of device
Jun 17 22:45:18 ubuntu kernel: [  297.509211] sda2: rw=0, want=18, limit=2
Jun 17 22:45:18 ubuntu kernel: [  297.514514] attempt to access beyond end of device
Jun 17 22:45:18 ubuntu kernel: [  297.514523] sda2: rw=0, want=3, limit=2
Jun 17 22:45:18 ubuntu kernel: [  297.515493] hfs: can't find a HFS filesystem on dev sda2.
Jun 17 22:45:18 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jun 17 22:45:18 ubuntu kernel: [  212.618295] cramfs: wrong magic
Jun 17 22:45:18 ubuntu kernel: [  212.628730] VFS: Can't find ext3 filesystem on dev sda5.
Jun 17 22:45:18 ubuntu kernel: [  212.633037] ReiserFS: sda5: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda5


```

I can't really tell if the partitioning scheme is bad or just the parameters you have tried to boot with...also looks like you have two other OSes? Fat and another linux distro?

Anyway ubiquity failed (so your installation is not good) with the above parameters,,,and possibly the above partition scheme. If you are manually partitioning, make sure you specify ext3 for the / (root) partition and he swap. reiserfs is ok for /var. You can always go with a default plan and move partitions later. Try acpi=off or noapic...not all three (acpi=off noapic nolapic) or acpi=off lapic.

good luck.

Thanks for all that...I certainly did not set acpi=off etc...as I would have no idea where to start...it was set when I choose the F6 (I think) and choose the ACPI work around. I can't even get it to install properly. There are two partitions (as you say) on this PC. One is empty and one contains Windows. I tried to do a full KDE4 install in the hope that that would clean the disk and set up new partitions...the problem was that the install failed. It will not even boot from the live CD. I am kind of at a loss to know what to do. I have already set up Kubuntu on an old IBM machine and it is working well - it was a breeze to set up. But the machine I am working on now is an oldish Asus...and I just cannot get any kind of install.

---

### Post by spiderbatdad on 2008-06-17
Sorry, I'm not familiar with "acpi workaround" as a kernel parameter. This is what it looks like on your kernel line...from syslog: ```
Kernel command line: debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet boot=casper ro debian-installer/locale=en_NZ.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  ** acpi=off noapic nolapic**
Jun 17 22:42:43 ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (013fd000)
``` Then a load of errors follow. So play around with different combos of those parameters, trying to boot the live cd...start with just acpi=off. I think that is the best bet. Then look at ```
dmesg
```After you reinstall, and the parameters can be adjusted accordingly. Maybe post dmesg here as an archive. ```
dmesg > ~/Desktop/dmesg.txt
```I wont be back until tomorrow. Maybe someone else will have a look, or you can pick up on the suggestions from the kernel on your own by reading through it. BTW, when you use acpi=off, delete "--quiet splash" from the end of the line.

---

### Post by dunbrokin on 2008-06-17
> **spiderbatdad said:**
> k. I see from syslog you have edited the boot line to read acpi=off noapic nolapic. This may be overkill. You may need local apic...you might want to try acpi=off lapic, or just acpi=off....takes a little experimenting.

Also looks like something is wrong in your partition scheme...created a reiserfs partition for /var? It may be full. IDK there are a lot of errors in the syslog...like this:

 ```
 >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
Jun 17 22:45:18 ubuntu kernel: [  297.509205] attempt to access beyond end of device
Jun 17 22:45:18 ubuntu kernel: [  297.509211] sda2: rw=0, want=18, limit=2
Jun 17 22:45:18 ubuntu kernel: [  297.514514] attempt to access beyond end of device
Jun 17 22:45:18 ubuntu kernel: [  297.514523] sda2: rw=0, want=3, limit=2
Jun 17 22:45:18 ubuntu kernel: [  297.515493] hfs: can't find a HFS filesystem on dev sda2.
Jun 17 22:45:18 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jun 17 22:45:18 ubuntu kernel: [  212.618295] cramfs: wrong magic
Jun 17 22:45:18 ubuntu kernel: [  212.628730] VFS: Can't find ext3 filesystem on dev sda5.
Jun 17 22:45:18 ubuntu kernel: [  212.633037] ReiserFS: sda5: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda5


```

I can't really tell if the partitioning scheme is bad or just the parameters you have tried to boot with...also looks like you have two other OSes? Fat and another linux distro?

Anyway ubiquity failed (so your installation is not good) with the above parameters,,,and possibly the above partition scheme. If you are manually partitioning, make sure you specify ext3 for the / (root) partition and he swap. reiserfs is ok for /var. You can always go with a default plan and move partitions later. Try acpi=off or noapic...not all three (acpi=off noapic nolapic) or acpi=off lapic.

good luck.

Ok, a new development...I have managed to install Ubuntu on the PC - a full and proper install and repartition the disk to suit Ubuntu....when I try to enter after the boot install, it still seems to hang..I reckon it is the ACPI problem again....I can now access the grub and root (not sure what the difference is ...anyway) so I guess in need to change something here to permanently set the ACPI off....so, where to from here?

Later: Ok managed to change one of the the boot lines to turn off ACPI and have Ubuntu properly installed (I can go from there to Kubuntu later)....but the graphic display is really shimmery and ghost like...is this a feature of ACPI off and is there any way of changing it.

---

### Post by dunbrokin on 2008-06-18
> **spiderbatdad said:**
> Sorry, I'm not familiar with "acpi workaround" as a kernel parameter. This is what it looks like on your kernel line...from syslog: ```
Kernel command line: debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet boot=casper ro debian-installer/locale=en_NZ.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  ** acpi=off noapic nolapic**
Jun 17 22:42:43 ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (013fd000)
``` Then a load of errors follow. So play around with different combos of those parameters, trying to boot the live cd...start with just acpi=off. I think that is the best bet. Then look at ```
dmesg
```After you reinstall, and the parameters can be adjusted accordingly. Maybe post dmesg here as an archive. ```
dmesg > ~/Desktop/dmesg.txt
```I wont be back until tomorrow. Maybe someone else will have a look, or you can pick up on the suggestions from the kernel on your own by reading through it. BTW, when you use acpi=off, delete "--quiet splash" from the end of the line.

Thank you for your help...we seem to be getting somewhere...attached the file you requested.

2 problems remain....the shimmery nature of the screen and the fact that the wireless card does not seem to be recognised.

---

### Post by spiderbatdad on 2008-06-18
Hi. I'm assuming you found the file /boot/grub/menu.lst that I talked about in post #2. This is where you edit the end of the kernel line to make your changes permanent. The kernel diagnostic is starting to look a little better.  I think you should remove "quiet splash" from the kernel line...as it stands, it looks like you have "quiet splash acpi=off."

Here is a message from the kernel:```
 PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   47.219155] PCI: No IRQ known for interrupt pin A of device 0000:01:05.0. **Please try using pci=biosirq.**
[   47.219168] NET: Registered protocol family 2
```

Also it looks like using acpi=off instead of the workaround has been good:
```
 Kernel command line: root=UUID=093a482d-7309-44be-8c87-55da14533ae2 ro quiet splash acpi=off
[    0.000000]** Found and enabled local APIC!**
``` You see how excited the kernel is to have found local apic.

What dmesg says is to try pci=biosirq, so you would edit /boot/grub/menu.lst with gksu gedit. like I showed in post #2, on the end of the line that starts with the word 'kernel,' you should delete "quiet splash. and add **acpi=off pci=biosirq** then save the file by clicking the floppy disk icon near the top of the window, and reboot.

The other problems are probably linked to this issue, as there are several messages where the pci interupts are unknown, but let's work on one thing at a time. Once this is booting correctly, if the video is still off, we'll look at the graphics card...same with wireless.

---

### Post by dunbrokin on 2008-06-18
> **spiderbatdad said:**
> Hi. I'm assuming you found the file /boot/grub/menu.lst that I talked about in post #2. This is where you edit the end of the kernel line to make your changes permanent. The kernel diagnostic is starting to look a little better.  I think you should remove "quiet splash" from the kernel line...as it stands, it looks like you have "quiet splash acpi=off."

Here is a message from the kernel:```
 PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   47.219155] PCI: No IRQ known for interrupt pin A of device 0000:01:05.0. **Please try using pci=biosirq.**
[   47.219168] NET: Registered protocol family 2
```

Also it looks like using acpi=off instead of the workaround has been good:
```
 Kernel command line: root=UUID=093a482d-7309-44be-8c87-55da14533ae2 ro quiet splash acpi=off
[    0.000000]** Found and enabled local APIC!**
``` You see how excited the kernel is to have found local apic.

What dmesg says is to try pci=biosirq, so you would edit /boot/grub/menu.lst with gksu gedit. like I showed in post #2, on the end of the line that starts with the word 'kernel,' you should delete "quiet splash. and add **acpi=off pci=biosirq** then save the file by clicking the floppy disk icon near the top of the window, and reboot.

The other problems are probably linked to this issue, as there are several messages where the pci interupts are unknown, but let's work on one thing at a time. Once this is booting correctly, if the video is still off, we'll look at the graphics card...same with wireless.

OK done....see attached.

---

### Post by spiderbatdad on 2008-06-18
I believe this is the video failing:```
intel8x0.c:2933: unable to grab IRQ 0
[   46.780601] Intel ICH: probe of 0000:00:1f.5 failed with error -16
[   47.824286] cs: IO port probe 0x100-0x3af: clean.
```

There is still a problem with irq routing...this for pin A and B:```
 No IRQ 
[   28.214900] known for interrupt pin B of device 0000:00:1f.6.
```

Perhaps edit the menu.lst again and try this: pci=routeirq (replace pci=biosirq) I have to leave, won't be back until tonight. Why are you using acpi=off?

Why don't you try this: **lapic pci=routeirq**just those two parameters. see how that goes.

---

### Post by dunbrokin on 2008-06-18
> **spiderbatdad said:**
> I believe this is the video failing:```
intel8x0.c:2933: unable to grab IRQ 0
[   46.780601] Intel ICH: probe of 0000:00:1f.5 failed with error -16
[   47.824286] cs: IO port probe 0x100-0x3af: clean.
```

There is still a problem with irq routing...this for pin A and B:```
 No IRQ 
[   28.214900] known for interrupt pin B of device 0000:00:1f.6.
```

Perhaps edit the menu.lst again and try this: pci=routeirq (replace pci=biosirq) I have to leave, won't be back until tonight. Why are you using acpi=off?

Why don't you try this: **lapic pci=routeirq**just those two parameters. see how that goes.

OK, thanks for your help...I will give it one last try...and then consign to the too hard basket...I spent enough time on this already. I used acpi=off as that is the only way I could get it to install. But I will try as you suggest and see what happens.

Later: no go...it just hangs at Setting up standard PCI resources.....nothing seems to make any operational difference apart form acpi=off. So unless somebody can come up with some new approaches, I am going to abandon the project. A big thanks to spiderbatdad for the help.

---

