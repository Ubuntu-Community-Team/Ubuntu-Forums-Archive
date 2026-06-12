---
title: "[SOLVED] Dual Booting with WIndows XP"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by newbpanda on 2008-11-12
I have the XP discs lying around somewhere but not sure if I've got 'em all. Anyhow, a friend ICQed me and was talking about Ubuntu. He said his guildmates had transfered to Ubuntu (he didn't mention I had first mentioned it to him) and they didn't miss XP that much.

When I tried to get back on Windows after re-installing Ubuntu (I had forgotten my user information or password), the computer just sits there when I instruct it to load from the hard drive its Windows partition. 

Here's how it works: Bios loads, I press F12 before the bar fills up. Then I select the hard drive from a list that also lists the floppy & CD-ROM as possible bootables. Next I select "Windows XP."

EDIT: How do I get WINE to recognize my 3D card? I have a GEFORCE 6200 with Direct X 9.0c.

---

### Post by handydan918 on 2008-11-12
> **newbpanda said:**
> I have the XP discs lying around somewhere but not sure if I've got 'em all. Anyhow, a friend ICQed me and was talking about Ubuntu. He said his guildmates had transfered to Ubuntu (he didn't mention I had first mentioned it to him) and they didn't miss XP that much.

When I tried to get back on Windows after re-installing Ubuntu (I had forgotten my user information or password), the computer just sits there when I instruct it to load from the hard drive its Windows partition. 

Here's how it works: Bios loads, I press F12 before the bar fills up. Then I select the hard drive from a list that also lists the floppy & CD-ROM as possible bootables. Next I select "Windows XP."
How did you install Ubu? Did you install GRUB Where?> 
EDIT: How do I get WINE to recognize my 3D card? I have a GEFORCE 6200 with Direct X 9.0c.Not gonna happen. Directx is for windows. It is a (surprise!) DIRECT interface with the hardware and will not work in another environment besides windows. The nvidia driver for linux supports 3D, though.

---

### Post by Bartender on 2008-11-12
OK, I'm familiar with the BIOS buttons like F12 or whatever that let you halt the boot process and pick a device.
Questions: 
Are you sure Windows partition is still there?
What happens if you just let the boot process run?  Do you not get to a DOS-looking screen (which is GRUB) giving you choices such as Ubuntu kernel so-and-so, Ubuntu recovery mode, and Windows XP bootloader (or something similar)?
Can you put the Ubuntu LiveCD back in again, boot from it, go to System>Administration>Gnome Partitioner and take a look at the partitions?  Make sure XP partition is still there?

---

### Post by eternalnewbee on 2008-11-12
> EDIT: How do I get WINE to recognize my 3D card
You should go to: **Main Menu > System > Administration > Hardware Drivers**, and activate your graphic card from there.

---

### Post by caljohnsmith on 2008-11-12
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by newbpanda on 2008-11-12
> **Bartender said:**
> O
Questions: 
Are you sure Windows partition is still there?
What happens if you just let the boot process run?  Do you not get to a DOS-looking screen (which is GRUB) giving you choices such as Ubuntu kernel so-and-so, Ubuntu recovery mode, and Windows XP bootloader (or something similar)?


Well, it used to list two Windows XP options (the second one didn't work) and then there was an option for Ubuntu. Now, after a lot of partitioning & re-partitioning it is as you described above. 

I think as it was installing Ubuntu, I read "deleting conflicting operating system files" or something like that pop up on the screen. 

I managed to find a thread that said something about the same card I've got so now I have NVIDIA running in my Ubuntu partition. I do know I've got a ton of software on the computer's primary hard drive (an 80GB it came with) and I didn't touch my secondary hard drive while I was partitioning (320GB). I might as well uninstall a bunch of that junk. I can look at the contents of my Windows stuff on my hard drives... can I use a program on Ubunutu to uninstall them???

When I get home from my social club, I'll post my partition info.

> **handydan918 said:**
> How did you install Ubu? Did you install GRUB Where?

I downloaded the latest version of Ubuntu. I think it was from the official website. It came as a ISO file & I used "IsoBuster" trail version to make it into a CD-ROM.

---

### Post by newbpanda on 2008-11-12
Okay. 

```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           80325    35407259    17663467+   5  Extended
/dev/sda4   *    35407260   156248189    60420465    7  HPFS/NTFS
/dev/sda5           80388      273104       96358+  82  Linux swap / Solaris
/dev/sda6          273168    35407259    17567046   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d170347

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS

```

No results for the second test suggested by CJS.

---

### Post by newbpanda on 2008-11-14
I re-installed Windows XP, now my computer can't connect to the internet or get back on ubunutu... which stinks.

---

### Post by newbpanda on 2008-11-15
Okay, so first I installed Windows XP then I installed Ubuntu again. Only problem is I can't use internet while using XP because it doesn't recognize my ethernet or the driver is not installed. 

No biggie I can just surf using Ubuntu & use XP for just gaming. No biggie.

---

