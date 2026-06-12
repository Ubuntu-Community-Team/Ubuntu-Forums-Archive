---
title: "Install not going so well...."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by pkjai1 on 2008-04-30
I have a computer that has 2 separate installations of Windows XP. This was the result of purchasing a new HD and installing windows on the new hard drive but I was too lazy to move the files from the old hard drive to the new one.

I'm trying to wipe the old hard drive, put Ubuntu on it and run a dual boot setup.

Now here's the problem:
I'm running the install off the Ubuntu CD I burned. Everything loads up fine but it keeps getting stuck at step 4 where it tries to load up the Partition manager. I restarted a few times hoping that it would just work some how but that, obviously , didn't work since I'm here.

I pull the slave hard drive (the newer hard drive) out of the computer and tried again. The partition manager part loads this time but it does not show the drive I've been trying to install it on. Its just a blank list, and no errors pop up.

The system setup:
CPU - P4 2.26
Mobo - Asus P4T533-C
Gfx Card - GeForce3 Ti 200
Memory - 512 MB RDRAM
HD - 80GB WD, 250 GB WD
Optical Drives - 2 NEC DVD Burners

If you know what's going on let me know. Thanks ^_^

Edit: I'm installing Ubuntu 8.04 btw.

---

### Post by janmartin on 2008-04-30
Do you use the Live CD?
If so, download, burn and try the alternate CD.

Good Luck.

BTW.:
Did you assemble the whole PC by yourself?

---

### Post by pkjai1 on 2008-04-30
Bump
(Impatient =])

---

### Post by martrn on 2008-04-30
> **pkjai1 said:**
>  [..] ... Now here's the problem:
I'm running the install off the Ubuntu CD I burned. Everything loads up fine but it keeps getting stuck at step 4 where it tries to load up the Partition manager. I restarted a few times hoping that it would just work some how but that, obviously , didn't work since I'm here.

OK you have two NEC DVD burners, and they are not reading the disk properly, or the disk you have burnt is corrupt or something.

Have you tried checking the CD to make sure the MD5 checksums work at properly and you do not have a corrupt image or a bad burn.


> **pkjai1 said:**
> 
I pull the slave hard drive (the newer hard drive) out of the computer and tried again. The partition manager part loads this time but it does not show the drive I've been trying to install it on. Its just a blank list, and no errors pop up.

The system setup:
CPU - P4 2.26
Mobo - Asus P4T533-C
Gfx Card - GeForce3 Ti 200
Memory - 512 MB RDRAM
HD - 80GB WD, 250 GB WD
Optical Drives - 2 NEC DVD Burners

If you know what's going on let me know. Thanks ^_^

Edit: I'm installing Ubuntu 8.04 btw.

I would recommend downloading the alternative CD and try running that, it runs in non graphical mode and you should be able to install ubuntu as it shouldn't run in a live environment and will not use DMA channels and you shouldn't have any problems in getting to install.

Make sure you check the CD image to make sure the MD5 checksums work out and you don't have a bad burn.

---

### Post by phread59 on 2008-04-30
Stupid question, are the drives in question IDE (ATA) or are they serial (SATA) drives.  If they are the former you must be sure to set the jumpers correctly.  On the back of the drive is a set of pins with a dongle you switch to determine if the drive is a primary or slave.  You need to set them to master no slave if you have only the 1 drive in it.  Also on the primary channel (hard drive channel) you need to be plugged into the end plug on the cable.  I believe it should be black.  The one crimped on the middle is for the slave.

If the cable or dongle is incorrectly placed you cannot get the computer to recognize it.  BTW there should be a picture of the positions on a tag on the drive to show you the dongle positions.  If everything is SATA all I gave you is for naught.  If everything is SATA I believe you're disc is corrupt.  Reburn the live CD image at a much slower rate.  And try a MD5checksum on the image and the disc.  I'm no good at that, there are tutorials out there for that.  And last but not least when prompted as to what you want to do, run live session, install ect.  Choose the option of checking the disc.  It could save you the hassle of trying to install with a bad disc.  I hope you get it fixed up fine.

Mark Shuman

---

### Post by pkjai1 on 2008-04-30
Well I don't have a bad burn.
Is there a way to run it with out the GUI using the Live CD I burned? I don't really feel like downloading it again.

---

### Post by martrn on 2008-04-30
> **pkjai1 said:**
> Well I don't have a bad burn.
Is there a way to run it with out the GUI using the Live CD I burned? I don't really feel like downloading it again.

If you are certain you have set up your hardware properly and you are certain you do not have a bad burn.

Then the only way to run it / the disk is to update the firmware of your dvd drive.  Check you have the latest firmware of your dvd drive, and that the manufacture has released the latest firmware and use unofficial firmware only if you have to.  Using unofficial firmware in your dvd drive may render your dvd hardware inoperable and invalidate any warentee you have for your hardware.

If that fails no the live cd maybe reading your drive incorrectly and setting things up that it prhaps best shouldn't and best way to work around this would be to use to alternative cd.

---

### Post by martrn on 2008-04-30
OK I just went to look at the communtity docs on the options you can have on boot up.

If you visit this site you can find them here.......
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

And go down until you find the kernel options....
You will find it says you can hit F6 on the boot menu and try...

[COLOR="SeaGreen"]**Option**[/COLOR]
Impact

[COLOR="SeaGreen"]**vga=xxx**[/COLOR]
Set your [WWW] framebuffer resolution to VESA mode xxx. Check [WWW] here for a list of possible modes.
[COLOR="SeaGreen"][B]
acpi=off OR noacpi[/B][/COLOR]
This parameter disables the whole ACPI system. This may prove very useful, for example, if your computer does not support ACPI or if you think the ACPI implementation might cause some problems (for instance random reboots or system lockups).

[COLOR="SeaGreen"]**acpi=force**[/COLOR]
Activates the ACPI system even if your computer BIOS date is older than 2000. This parameter overwrites acpi=off and can also be used with current hardware if the ACPI support is not activated despite apm=off.
[COLOR="SeaGreen"][B]
pci=noacpi OR acpi=noirq[/B][/COLOR]
These parameters disable the PCI IRQ routing

[COLOR="SeaGreen"]**pci=acpi**[/COLOR]
This parameter activates the PCI IRQ routing
[COLOR="SeaGreen"][B]
acpi_irq_balance[/B][/COLOR]
ACPI is allowed to use PIC interrupts to minimize the common use of IRQs.

[COLOR="SeaGreen"]**acpi_irq_nobalance**[/COLOR]
ACPI is not allowed to use PIC interrupts.
[COLOR="SeaGreen"][B]
acpi=oldboot[/B][/COLOR]
Deactivates the ACPI system almost completely; only the components required for the boot process will be used.

[COLOR="SeaGreen"]**acpi=ht**[/COLOR]
Impact Deactivates the ACPI system almost completely; only the components required for hyper threading will be used.

[COLOR="SeaGreen"]**noapic**[/COLOR]
Disable the "Advanced Programmable Interrupt Controller (APIC)".

[COLOR="SeaGreen"]**nolapic**[/COLOR]
Disable the "local APIC".

apm=off OR noapm
Disable the Advanced Power Management.

[COLOR="SeaGreen"]**irqpoll**[/COLOR]
Changes the way the kernel handles interrupt calls (set it to [WWW] polling). Can be useful in case of hardware interrupt issues.

---

### Post by pkjai1 on 2008-04-30
Alright. Now I have a new problem. I pulled the smaller hard drive out and wiped the partition on another computer. Then I plugged it back into the computer I'm trying to install ubuntu on.

Now it won't boot from the Live CD at all. It's giving me the "PRESS A KEY TO REBOOT." message.

I'm sure I have the jumpers correct and the IDE cables correct. The CD was verified previously so I dont have a bad burn. I have also reset the BIOS and i have the boot sequence settings correct.

So if anybody could help out that would be great.

Edit: I almost forgot. It boots from the Windows Setup CD but not the Ubuntu disk.

---

### Post by martrn on 2008-04-30
> **pkjai1 said:**
> Alright. Now I have a new problem. I pulled the smaller hard drive out and wiped the partition on another computer. Then I plugged it back into the computer I'm trying to install ubuntu on.

Now it won't boot from the Live CD at all. It's giving me the "PRESS A KEY TO REBOOT." message.

I'm sure I have the jumpers correct and the IDE cables correct. The CD was verified previously so I dont have a bad burn. I have also reset the BIOS and i have the boot sequence settings correct.

So if anybody could help out that would be great.

A live CD is not an ideal environment to boot from.  
I fully recommend janmartin's idea of downloading and installing from the alternative environment.  

To clarifiy, I don't doubt there is anything wrong with your hardware, just that a live environment, does't work for all computer systems.

---

### Post by pkjai1 on 2008-04-30
I'm downloading the Alternative disk as we speak. I'll let you know how it works out.

---

### Post by pkjai1 on 2008-05-01
Alright. NEW ERROR!!! lol
I got though the install, but now it ends with a Squashfs error.
Gonna try the install again and see what happens.

---

### Post by martrn on 2008-05-01
OK you have two NEC DVD burners, two seperate install disks and they are not reading the disk properly, or the DVD burners are not sending the data properly.
(Squashfs error).

I agree with your title....
Your Install is not going so well at all....

OK Look at the communtity docs on the options you can have different boot option.  If you visit this site you can find them here.......
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

And go down until you find the kernel options....
You will find it says you can hit F6 on the boot menu and try...

ide=nodma

---

