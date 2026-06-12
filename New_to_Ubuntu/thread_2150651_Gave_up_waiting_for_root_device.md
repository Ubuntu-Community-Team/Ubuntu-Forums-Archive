---
title: "Gave up waiting for root device"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by hyudryu on 2013-06-01
So ubuntu has been working fine on my Acer aspire S3 for around 2 weeks. One day when I tried to boot it up, it gave me this error. 


[IMG]http://i1201.photobucket.com/albums/bb357/hyudryu/photo10_zps3764be64.jpg[/IMG]

So I have no choice but to boot to Windows. Is there any way to fix this problem? I noticed that the ubuntu windows boot selection menu no longer has a 10 second time limit anymore. And when I boot to linux, my hard drive doesn't spin at all.

---

### Post by hyudryu on 2013-06-02
Bump

---

### Post by ahallubuntu on 2013-06-02
Ubuntu tried to boot but it could not find your root partition - UUID ac5dblahblahblah.  There are various reasons for this happening, but usually something like this would happen after a failed update or a manual change made incorrectly.  It shouldn't simply happen if you've done nothing unusual.

Did you do any updates or make changes right before this happened?

I'd boot your Ubuntu live USB/live CD and try a few things.  First, to be safe, I'd check your hard drive's S.M.A.R.T. status.  Install GSmartControl from the live session, start it up, then look at the Attributes tab.  Any Attributes highlighted in pink or red?  If so, those may indicate serious problems on your disk.

You should also check your /etc/fstab file (which tells Ubuntu what partitions to mount when you are booting up).  Mount your main Ubuntu partition if you can and look for the etc/fstab file (note: it will be under /media/something... depends what version of Ubuntu you are using.  But the file /etc/fstab is the one from the LIVE session - you want to find this file under /media....whatever/etc/fstab that's on the Ubuntu installation disk, not in the live session.

Also, what's the output of this command (open a terminal with Ctrl Alt t):

sudo blkid

We'll want to compare that to the contents of your fstab file.

---

### Post by hyudryu on 2013-06-02
Well, before the problem occured, I went back onto windows to edit a video for my finals project, and all I installed/updated was the film editing software. When I tried booting back to Ubuntu, it gave me that error.  I'll try what you suggested and then get post my results here.

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]hyudryu; Hi !

Before getting too paniced... re-read the errors preamble ...maybe this one instance is but a race condition. It happens to me on occasion -particularly switching between installs - entering "exit' at the prompt and rebooting generally resolves it for me .

Is booting to the initramfs prompt a frequent thing ?
[/COLOR][INDENT=2][COLOR=#000000]
it is all a learning experience

[/COLOR][/INDENT]
[INDENT=4][COLOR=#000000]
 [/COLOR][/INDENT]

---

### Post by matt_symes on 2013-06-02
Hi

Besides the other good answers for you to check, i'm going to offer another.

I'm interested in the modprobe timeout message you are getting along with dropping to the busybox prompt.

The modprobe command is used to load drivers into the kernel to control your hardware. I have been doing some checking on my system.

The error you are getting is (paraphrased)

```
... timeout ... /sbin/modprobe pci:v00008086d00001c03sv00001025sd00000635......
```

```
v0000**8086**d0000**1c03**
```

The 2 numbers i have bolded are the vendor id and the device id of the hardware that modprobe is trying to load the driver for.

It's your sata ahci driver for your hard drive controller.

From...

[http://cateee.net/lkddb/web-lkddb/SATA_AHCI.html](http://cateee.net/lkddb/web-lkddb/SATA_AHCI.html)

> [LEFT][COLOR=#000000][FONT=Times New Roman]vendor: [/FONT][/COLOR][/LEFT]
**8086**[LEFT][COLOR=#000000][FONT=Times New Roman]("[/FONT][/COLOR][/LEFT]
[I]Intel Corporation[LEFT][COLOR=#000000][FONT=Times New Roman]"), device: [/FONT][/COLOR][/LEFT]
**1c03**[LEFT][COLOR=#000000][FONT=Times New Roman]("[/FONT][/COLOR][/LEFT]
[I]6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller[LEFT][COLOR=#000000][FONT=Times New Roman]")[/FONT][/COLOR][/LEFT]
[/I][/I]

That's interesting because it's dropping you to the initramfs prompt because it cannot find the root filing system on your hard drive and the sata ahci controller talks to the hard drive where the root filing system resides.

A search for the driver on my laptop using the device ids returns this
```

matthew-S206:/home/matthew/storage/linux_source/initramfs % grep -i "v00008086d00001c03" /lib/modules/$(uname -r)/modules.alias
alias pci:v00008086d00001C03sv*sd*bc*sc*i* ahci
matthew-S206:/home/matthew/storage/linux_source/initramfs % 
```

So the achi driver gets loaded when modprobe is called with that long string of characters. 

This driver is part of the initramfs filing system as well as on your root partition. 

The initial ram filing system (initramfs) is loaded at startup and is used to load drivers necessary to mount the root filing system.

Extracting my initamfs and searching for the ahci driver..

```
mkdir initramfs && cd $_ && zcat /boot/initrd.img-3.9.0-3-generic | cpio -i && find . -name "*ahci*"
```

returns this...

```

matthew-S206:/home/matthew/storage/linux_source % mkdir initramfs && cd $_ && zcat /boot/initrd.img-3.9.0-3-generic | cpio -i && find . -name "*ahci*"
165362 blocks
./lib/modules/3.9.0-3-generic/kernel/drivers/ata/libahci.ko
./lib/modules/3.9.0-3-generic/kernel/drivers/ata/ahci_platform.ko
./lib/modules/3.9.0-3-generic/kernel/drivers/ata/ahci.ko
./lib/modules/3.9.0-3-generic/kernel/drivers/ata/acard-ahci.ko
matthew-S206:/home/matthew/storage/linux_source/initramfs %
```

My initramfs contains the ahci drivers and on my machine they are modprobed into the kernel. I am not sure if that happens during initramfs or after the root filing system is loaded though.

```

matthew-S206:/home/matthew % lsmod | grep ahci
ahci                   25819  5 
libahci                31898  1 ahci
matthew-S206:/home/matthew %
```

I wondering if this is why you are being dropped to the initramfs prompt; initramfs cannot load the ahci drivers to mount your root filing system.

Have you had a kernel update and can you boot into that older kernel from the grub menu ?

Can you manually modprobe the driver from the initramfs prompt and does that help if you continue the boot process ? Does you initramfs contain the ahci and libahci modules ?

This is speculation on my part as i have never had a modprobe timeout during initramfs but it may be worth exploring further.

Kind regards

---

### Post by hyudryu on 2013-06-06
> **Bashing-om said:**
> [COLOR=#000000]hyudryu; Hi !

Before getting too paniced... re-read the errors preamble ...maybe this one instance is but a race condition. It happens to me on occasion -particularly switching between installs - entering "exit' at the prompt and rebooting generally resolves it for me .

Is booting to the initramfs prompt a frequent thing ?
[/COLOR][INDENT=2][COLOR=#000000]
it is all a learning experience

[/COLOR][/INDENT]
[INDENT=4][COLOR=#000000]
[/COLOR][/INDENT]

Oh it's every time. I can't even boot into linux :(
Edit: entering exit just makes it freeze at the error place. It doesn't let me boot in.

---

### Post by hyudryu on 2013-06-09
> **ahallubuntu said:**
> Ubuntu tried to boot but it could not find your root partition - UUID ac5dblahblahblah.  There are various reasons for this happening, but usually something like this would happen after a failed update or a manual change made incorrectly.  It shouldn't simply happen if you've done nothing unusual.

Did you do any updates or make changes right before this happened?

I'd boot your Ubuntu live USB/live CD and try a few things.  First, to be safe, I'd check your hard drive's S.M.A.R.T. status.  Install GSmartControl from the live session, start it up, then look at the Attributes tab.  Any Attributes highlighted in pink or red?  If so, those may indicate serious problems on your disk.

You should also check your /etc/fstab file (which tells Ubuntu what partitions to mount when you are booting up).  Mount your main Ubuntu partition if you can and look for the etc/fstab file (note: it will be under /media/something... depends what version of Ubuntu you are using.  But the file /etc/fstab is the one from the LIVE session - you want to find this file under /media....whatever/etc/fstab that's on the Ubuntu installation disk, not in the live session.

Also, what's the output of this command (open a terminal with Ctrl Alt t):

sudo blkid

We'll want to compare that to the contents of your fstab file.

I can't boot into linux in the first place. I'm using windows to try to find out my hard drive's SMART status.

---

### Post by hyudryu on 2013-06-09
> **matt_symes said:**
> Hi

Besides the other good answers for you to check, i'm going to offer another.

I'm interested in the modprobe timeout message you are getting along with dropping to the busybox prompt.

The modprobe command is used to load drivers into the kernel to control your hardware. I have been doing some checking on my system.

The error you are getting is (paraphrased)

```
... timeout ... /sbin/modprobe pci:v00008086d00001c03sv00001025sd00000635......
```

```
v0000**8086**d0000**1c03**
```

The 2 numbers i have bolded are the vendor id and the device id of the hardware that modprobe is trying to load the driver for.

It's your sata ahci driver for your hard drive controller.

From...

[http://cateee.net/lkddb/web-lkddb/SATA_AHCI.html](http://cateee.net/lkddb/web-lkddb/SATA_AHCI.html)



That's interesting because it's dropping you to the initramfs prompt because it cannot find the root filing system on your hard drive and the sata ahci controller talks to the hard drive where the root filing system resides.

A search for the driver on my laptop using the device ids returns this
```

matthew-S206:/home/matthew/storage/linux_source/initramfs % grep -i "v00008086d00001c03" /lib/modules/$(uname -r)/modules.alias
alias pci:v00008086d00001C03sv*sd*bc*sc*i* ahci
matthew-S206:/home/matthew/storage/linux_source/initramfs % 
```

So the achi driver gets loaded when modprobe is called with that long string of characters. 

This driver is part of the initramfs filing system as well as on your root partition. 

The initial ram filing system (initramfs) is loaded at startup and is used to load drivers necessary to mount the root filing system.

Extracting my initamfs and searching for the ahci driver..

```
mkdir initramfs && cd $_ && zcat /boot/initrd.img-3.9.0-3-generic | cpio -i && find . -name "*ahci*"
```

returns this...

```

matthew-S206:/home/matthew/storage/linux_source % mkdir initramfs && cd $_ && zcat /boot/initrd.img-3.9.0-3-generic | cpio -i && find . -name "*ahci*"
165362 blocks
./lib/modules/3.9.0-3-generic/kernel/drivers/ata/libahci.ko
./lib/modules/3.9.0-3-generic/kernel/drivers/ata/ahci_platform.ko
./lib/modules/3.9.0-3-generic/kernel/drivers/ata/ahci.ko
./lib/modules/3.9.0-3-generic/kernel/drivers/ata/acard-ahci.ko
matthew-S206:/home/matthew/storage/linux_source/initramfs %
```

My initramfs contains the ahci drivers and on my machine they are modprobed into the kernel. I am not sure if that happens during initramfs or after the root filing system is loaded though.

```

matthew-S206:/home/matthew % lsmod | grep ahci
ahci                   25819  5 
libahci                31898  1 ahci
matthew-S206:/home/matthew %
```

I wondering if this is why you are being dropped to the initramfs prompt; initramfs cannot load the ahci drivers to mount your root filing system.

Have you had a kernel update and can you boot into that older kernel from the grub menu ?

Can you manually modprobe the driver from the initramfs prompt and does that help if you continue the boot process ? Does you initramfs contain the ahci and libahci modules ?

This is speculation on my part as i have never had a modprobe timeout during initramfs but it may be worth exploring further.

Kind regards

I booted into Ubuntu using my USB, and I found fstab in etc.
It seems to be able to find my hard drive and also the picture shows the blkid output from terminal
What should I do next?



[IMG]http://i.imgur.com/kHI0fQy.png[/IMG]

---

### Post by matt_symes on 2013-06-10
Hi

Firstly run fsck from the LiveUSB and try to boot into your installation.

Secondly, can you boot into an older kernel from the grub menu on you installation ?

If you can then try rebuilding you initramfs for the new kernel from the old kernel.

If you cannot the try chrooting into your installation from the LiveUSB and rebuilding it from there.

Kind regards

---

