---
title: "Dual boot Ubuntu w/ RHEL installed w/ LVM"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by neurostu on 2008-06-04
So I currently have a machine with RHEL 5 installed with LVM. I would like to insert another HDD into my machine and install Ubuntu onto that drive. However I'm not sure how to do this without disrupting my current RHEL LVM install.

Does anybody have any experience with this?

---

### Post by Duck2006 on 2008-06-04
Install ubuntu on the fresh drive and install grub to the MBR of the fresh drive, then edit the grub boot loader of RHEL 5 to boot ubuntu.

---

### Post by neurostu on 2008-06-04
So I'm trying to remember how to get the RHEL grub install to point to the ubuntu install, any help?  I'm trying google but I can't seem to form my query correctly.

---

### Post by Duck2006 on 2008-06-04
Go into rhel and login as root go to system (or computer, been that long) /boot/grub and look for the grub.conf file, edit it save it. I think that how you can get it done in red hat.

---

### Post by neurostu on 2008-06-04
ya... I guess RHEL made a /boot/ parition, I found it.
So I was just going to copy the the meny.lst from my ubuntu install and paste the relevant parts into the menu.lst in my RHEL grub.... but both of them have 
```

root   (hd0,0)

```

So I'm not sure exactly what to do there, as I thought I had to tell grub which HDD the kernel is on... don't i?

---

### Post by Duck2006 on 2008-06-04
This may help.

[http://www.cyberciti.biz/faq/linux-serial-console-howto/](http://www.cyberciti.biz/faq/linux-serial-console-howto/)

---

### Post by Duck2006 on 2008-06-04
> **neurostu said:**
> ya... I guess RHEL made a /boot/ parition, I found it.
So I was just going to copy the the meny.lst from my ubuntu install and paste the relevant parts into the menu.lst in my RHEL grub.... but both of them have 
```

root   (hd0,0)

```

So I'm not sure exactly what to do there, as I thought I had to tell grub which HDD the kernel is on... don't i?

No rhel will have root (hd0,0)
Ubuntu will have root (hd1,0)

---

### Post by neurostu on 2008-06-04
I found the ubuntu drive under /dev/  
```

sdc1 --> /
sdc2 --> /home
sdc3 --> swapspace

```
so would I use root (hd2,0)?

btw.. thanks for the link, but it looks like it has to do with using your modem over grub

---

### Post by Duck2006 on 2008-06-04
Run fdisk -l in the terminal, not sure you may have to run su -l first then run fdisk -l to see the drives, but i think it would have to be root (hd1,0)

---

### Post by neurostu on 2008-06-04
fdisk gave me:

```

[root@stockton ~]# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       60801   488279610   8e  Linux LVM

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   8e  Linux LVM

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2805    22531131   83  Linux
/dev/sdc2            2806       29849   217230930   83  Linux
/dev/sdc3           29850       30401     4433940   82  Linux swap / Solaris

```

---

### Post by Duck2006 on 2008-06-04
sda = root (hd0,0)
sdb = root (hd1,0)
sdc = root (hd2,0)

So yes if ubuntu is on sdc then root would be (hd2,0)

---

### Post by neurostu on 2008-06-04
So tried pasting the lines from the ubuntu menu.lst and put them in the RHEL menu.lst, changing the (hd0,0) to (hd2,0). I then had to remove the root=UUID="somelongword" line to get it to boot, but now I am getting a lot of :

```

ata2: port is slow to respond....

```

it went through that for about 2 minutes, then it booted to:

```

(initramfs)

```
with a blinking cursor...

I'm pretty sure I didn't do it right...

---

### Post by neurostu on 2008-06-04
btw I really appreciate your help!

---

### Post by Duck2006 on 2008-06-04
Try

root (hd2,0)
chainloader +1

or

rootnoverify (hd2,0)
chainloader +1

that should pass from the red hat boot loader to the ubuntu boot loader to load ubuntu.

---

### Post by neurostu on 2008-06-04
I tried both options and I got:
```

Error 13: invalid or unsupported executable format

```

I also tried placing the new HDD at the top of the BIOS boot list.

---

### Post by Duck2006 on 2008-06-04
> **neurostu said:**
> I tried both options and I got:
```

Error 13: invalid or unsupported executable format

```

I also tried placing the new HDD at the top of the BIOS boot list.

If you change the drive in you BOIS then you should be able to boot into ubuntu (if you install grub from ubuntu to the MBR of that drive). The only other thing i can put forth id try linuxquestions.org they get a thew red hat people in there.

---

### Post by neurostu on 2008-06-04
Ok so this is the stupidest problem ever. I checked my MOBO and I guess I have 4 sata ports reserved for the on board raid controller. I plugged my HDD into a different port and it booted just fine, when I placed the new HDD above the old one in the BIOS.  Now I'm going to try getting my ubuntu grub to point to my RHEL grub.

---

### Post by Duck2006 on 2008-06-04
> **neurostu said:**
> Ok so this is the stupidest problem ever. I checked my MOBO and I guess I have 4 sata ports reserved for the on board raid controller. I plugged my HDD into a different port and it booted just fine, when I placed the new HDD above the old one in the BIOS.  Now I'm going to try getting my ubuntu grub to point to my RHEL grub.

When you installed rhel 5, did it setup a boot partition, so you can boot  the LVM partition?

---

### Post by neurostu on 2008-06-04
I believe it did. When I was editing the RHEL grub menu.lst it said something about there being a boot partition in there. When I examine the HDD's under GParted it says that the first of the LVM HDDs has two partitions on it and the second only has 1.

Right now I am going to use the bios to select the OS I am going to use.  I won't be switching between the two that much. Maybe one day I'll get brave enough to start messing with grub again, and I'll figure it out!

Thanks again for your help

---

### Post by Duck2006 on 2008-06-04
Ok find out what partition the / boot partition and point grub in ubuntu to that partition.

root (x,y)
chainloader +1

and that should pass the boot to the boot loader of red hats boot partition.

---

### Post by neurostu on 2008-06-04
Great thanks!

Do you know what the
```

makeactive

```
command does?

---

### Post by Duck2006 on 2008-06-04
From the Grub Manual

> 
makeactive [Command]
Set the active partition on the root disk to GRUB’s root device. This command is limited to primary PC partitions on a hard disk.

---

