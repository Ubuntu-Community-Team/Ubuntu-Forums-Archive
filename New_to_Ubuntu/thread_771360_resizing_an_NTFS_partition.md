---
title: "resizing an NTFS partition"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by rockerphil on 2008-04-27
ok, i'm currently running Fluxbuntu on my old Dell Dimension desktop having previously switched from Windows 2000. well i currently have all my music and family photos on my 2nd hard drive which is formatted to an NTFS file system. i would move them to my primary hard drive which is of course on a Linux ext2 ext3 and ext5 partition, but i don't have the space. i have tried resizing the partition with Gparted, but it won't allow me to resize even while logged in as root, and i dont have a CD burner, so i can't boot from the gparted live CD and do it that way. so if someone could plz suggest either a different program to resize my NTFS partition or a partition editing program that could be booted from a floppy it would be greatly appreciated.

---

### Post by mlentink on 2008-04-27
rockerphil,
I really wish I could help you, but there's absolutely no way you can change the size of an active partition. I advise to get someone wih a cd burner to burn you a Ubuntu Live CD, which includes GParted. Unmount any partitiions on your current system, and then try to change sizes, if at all possible

---

### Post by rockerphil on 2008-04-27
i can easily unmount the partition. that's not the issue. i'm simply looking for some type of partition editing software that can be booted from a boot floppy (yes, i know, i'm out of date)

---

### Post by Oldsoldier2003 on 2008-04-27
> **rockerphil said:**
> i can easily unmount the partition. that's not the issue. i'm simply looking for some type of partition editing software that can be booted from a boot floppy (yes, i know, i'm out of date)

if you have usb there is a gpaarted live usb [http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

---

### Post by rockerphil on 2008-04-27
my BIOS doesn't support booting from a USB stick. the original OS on this machine was Windows 98se

---

### Post by kk0sse54 on 2008-04-27
Have you tried partition logic or Fdisk, both which boot from a floppy?

---

### Post by Oldsoldier2003 on 2008-04-27
> **rockerphil said:**
> my BIOS doesn't support booting from a USB stick. the original OS on this machine was Windows 98se
Perhaps Ranish? have a look and see if its something that might interest you.
[http://www.ranish.com/part/](http://www.ranish.com/part/)

---

### Post by mlentink on 2008-04-27
Are you really sure there is noone in your neighbourhood that could burn a live-cd for you? Because if you could, GParted is included on that Live-CD...

---

