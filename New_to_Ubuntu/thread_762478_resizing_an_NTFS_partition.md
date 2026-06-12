---
title: "resizing an NTFS partition"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by rockerphil on 2008-04-22
ok, here's the deal. i've been running Fluxbuntu on my computer for about 6 months now and am loving it, but here's the problem, i've got an 8 GB hard drive that my OS is installed on and a 2nd 40 GB hard drive that's got all my family photos and music on an NTFS partition, and i'd like to move them to an ext2/3 partition, but gparted (the Gnome Partition Editor) won't allow me to resize the NTFS partition so that i can start trnansfering my files to a Linux partition. any help would be appreciated.

---

### Post by billgoldberg on 2008-04-22
> **rockerphil said:**
> ok, here's the deal. i've been running Fluxbuntu on my computer for about 6 months now and am loving it, but here's the problem, i've got an 8 GB hard drive that my OS is installed on and a 2nd 40 GB hard drive that's got all my family photos and music on an NTFS partition, and i'd like to move them to an ext2/3 partition, but gparted (the Gnome Partition Editor) won't allow me to resize the NTFS partition so that i can start trnansfering my files to a Linux partition. any help would be appreciated.

You will need to unmount the drive before you can resize/format.

If you use the gparted live cd, that shouldn't be an issue.

---

### Post by rockerphil on 2008-04-22
i don't have a CD burner, so booting from a live CD isn't an option. do you know of any bootable partition software that can be run from a floppy?

---

### Post by billgoldberg on 2008-04-22
> **rockerphil said:**
> i don't have a CD burner, so booting from a live CD isn't an option. do you know of any bootable partition software that can be run from a floppy?

It can be done with the ubuntu live cd also. So if you have that one, try it.

As for the floppy thing, I don't have a clue, haven't used a floppy in years.

---

### Post by rockerphil on 2008-04-22
as i said, i don't have a CD burner and i run Fluxbuntu, which for some reason is just an install CD, not a Live CD but thanx anyways, and no, even unmounted i can't resize the partition

---

### Post by faytaliti on 2008-04-22
Why don't you try G parted. If you don't know what that means, it's a live CD containing an extremely powerful partition editor. Try it out. it's easily available on a Google search. Go on and get cracking ! :popcorn:

---

### Post by PmDematagoda on 2008-04-22
Actually, you can do it through normal Ubuntu(Fluxbuntu in your case) by installing Gparted and ntfsprogs:-
```
sudo apt-get install gparted
```
```
sudo apt-get install ntfsprogs
```

That should allow you to resize NTFS partitions.

---

### Post by wolfhabits1 on 2009-09-19
Can you boot a live-cd image from a USB device?
[Unetbootin]("http://unetbootin.sourceforge.net/") can be use with a live cd .iso to make a bootable usb drive.

If you got a distro .iso with gparted, and got a 1gb usb drive handy, i'd give it a shot.
I tested the windows version, and it works real well. There is a version for Linux too, I bet it works fine.

Once the drive is setup, you can boot from USB and partition to your hearts content. :)

Ubuntu really needs to integrate a usb installer into their live-cd :) Especially if it's part of the autorun in windows. 
Ubuntu Live CD --> create LiveUSB
That would be win.

---

