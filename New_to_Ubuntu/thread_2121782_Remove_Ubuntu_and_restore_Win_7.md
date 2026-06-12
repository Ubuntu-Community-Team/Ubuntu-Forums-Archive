---
title: "Remove Ubuntu and restore Win 7"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by JihadTurtle on 2013-03-03
Well, crap. I can't use this OS, and I did a full install. Can I do a factory reset to get me back to windows 7? I try doing f8 or f12 during the boot, and it doesn't take me to the Intel boot options where you find reset to factor defaults or whatever. Is it possible to reset EVERYTHING on the PC? Also, I do not have an install disk.

---

### Post by QIII on 2013-03-03
When you installed Ubuntu -- or attempted to -- did you create a new partition table and allow the partitioning tool to run?

---

### Post by JihadTurtle on 2013-03-03
I did not create a partition.

---

### Post by carl4926 on 2013-03-03
> **JihadTurtle said:**
> Well, crap. I can't use this OS, and I did a full install. Can I do a factory reset to get me back to windows 7? I try doing f8 or f12 during the boot, and it doesn't take me to the Intel boot options where you find reset to factor defaults or whatever. Is it possible to reset EVERYTHING on the PC? Also, I do not have an install disk.

Do you currently have an option to boot windows?

---

### Post by JihadTurtle on 2013-03-03
> **carl4926 said:**
> Do you currently have an option to boot windows?

Nope.

---

### Post by carl4926 on 2013-03-03
Open a terminal and post the result of

```
sudo fdisk -l
```That's a lower case L not a number 1

---

### Post by QIII on 2013-03-03
And we might ask you to follow the instructions [here](https://help.ubuntu.com/community/Boot-Info) to give us some more info after we take a look at what you were just asked for.

---

### Post by JihadTurtle on 2013-03-03
> **carl4926 said:**
> Open a terminal and post the result of

```
sudo fdisk -l
```That's a lower case L not a number 1

Here it is:
```


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda:750.2 GB, 750156374014 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 52 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimum): 4096 bytes / 4096 bytes
Disk identifier: 0xc3664e96
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

```


EDIT: It just occured to me that you guys might think my OS is broken. It's not, I'm just lost as hell in it and want to switch back.

---

### Post by carl4926 on 2013-03-03
> **QIII said:**
> And we might ask you to follow the instructions [here]("https://help.ubuntu.com/community/Boot-Info") to give us some more info after we take a look at what you were just asked for.


Please follow this advice
fdisk info was no use really as you have GPT

---

### Post by QIII on 2013-03-03
No.  I wasn't under the impression that your system was broken.

I just figured you wanted to go back to Windows, which is a perfectly fair desire.  Nobody can fault you for that.  You should use what works for you and what is comfortable.  I, for one, still use Windows 7 as well.  I'm not a Linux zealot and I won't try to discourage you from that.  

What we are afraid of is that if you either created a new partition table or chose "Use entire disk" when you installed, that you have completely nuked your Windows.

If you have done that, it may cost you some money to get a new retail Windows disk -- but I really hope we can do this without costing you anything!

I have to get to bed now.  But this is a worldwide community, so there is probably someone who can continue on.

Good luck.  I'll try to check in on this tomorrow if I have time.

---

### Post by JihadTurtle on 2013-03-03
I can't install the boot repair thingy. It just doesn't show up.

---

### Post by darkcrimson on 2013-03-03
The output from fdisk is only showing a placeholder partition.
Since this partition is GPT, we'll need to use parted instead. Please copy+paste the output of this command:

```

parted /dev/sda print
```

> I can't install the boot repair thingy. It just doesn't show up.

Try [this]("https://help.ubuntu.com/community/LinuxSecureRemix?action=show&redirect=UbuntuSecureRemix") instead. Make sure to download the correct version for your Ubuntu installation (i.e. 32-bit or 64-bit)

---

### Post by carl4926 on 2013-03-03
Can you post

```
sudo parted -l
```

---

### Post by JihadTurtle on 2013-03-03
I opened up GRUB once, and now I want to boot to an install disk for Windows 7 Ultimate, but I can't seem to get GRUB to open. Is there a special button I press? I thought I did it with f8 last time, but it doesn't work now.

---

### Post by Cheesemill on 2013-03-03
It isn't GRUB you're looking for, it's your computers BIOS settings.

GRUB is loaded *after* the computer starts booting from your hard drive, at this point it is too late to boot from the Windows installation DVD.
The method for accessing your BIOS varies from manufacturer to manufacturer, but it involves pressing a certain key as soon as you switch on your machine. It's usually one of the function keys or delete but you'll have to check the instructions that came with your machine/motherboard to find out for sure. Usually a quick google for the model number of your machine and the word BIOS will let you know which key to press.

---

### Post by JihadTurtle on 2013-03-03
I finally found out how to get into my BIOS and boot from my install disk, but all of my hard drive partitions are formatted incorrectly. How can I reformat them? Also, there is only one with enough space, and it has Ubuntu on it. Is it safe to install over top of Ubuntu? How do I delete Ubuntu?

---

### Post by QIII on 2013-03-03
[I]Several threads [B]merged.  


[/B][/I]Edited subject

---

### Post by JihadTurtle on 2013-03-03
GENERAL UPDATE:

I screwed up. I deleted any trace of Windows from my PC. Now I need to reformat my hard drive to NTFS format. Can I do that from my BIOS? It says I cannot partition or clear and reformat my hard drive while in Ubuntu because it's being used, and I don't have my Ubuntu CD. Help?

---

### Post by Cheesemill on 2013-03-03
You can use the Windows installation disc to reformat your drive.

When you get to the stage of the installation where you choose where to install Windows just click on 'Advanced' and then delete the Ubuntu partitions. You can then select the now unallocated space to install Windows on to.

---

### Post by darkcrimson on 2013-03-03
You can do it from either a Windows 7 install DVD or an Ubuntu live cd/dvd using Gparted. Unfortunately, the BIOS will not be able to help you in that regard.

---

### Post by QIII on 2013-03-03
I'm sorry this has turned into a such a painful chore!

If the Windows installation disk will not work (it may tell you the disk is in an unknown format), just download and burn another copy of the .iso and boot with it.  When booted to a live session, your hard drive will not be mounted and you can change the partition table from there.  Make a single, large NTFS partition to begin with and your Windows installation disk should take it from there.

Again, best wishes!

---

