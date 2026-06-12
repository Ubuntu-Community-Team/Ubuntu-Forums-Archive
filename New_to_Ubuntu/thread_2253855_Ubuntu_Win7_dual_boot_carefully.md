---
title: "Ubuntu Win7 dual boot carefully"
date: 2014-11-22
forum: New to Ubuntu
---

### Post by ray9 on 2014-11-22
So I know this topic has been ridden into the ground.  But I'm being very careful.  I shrank my win7 partition with the win7 disk management tool and it went fine.  Downloaded 14.04 trusty 64 bit on a flash drive.  Clicked install Ubuntu and then clicked "something else".  So here I  am:  Freespace 360 G, "Device for bootloader installation ATA ST750LM022 HN-M7 (750.2GB)  INSTALL NOW!  Not so fast.  I have to run this by the ones who have been there, done that.

Device:
/dev/sda
free space
/dev/sda1 fat32
/devsda2
/dev/sda3 ntfs
freespace 360,000 MB

Click "Install Now" ????

---

### Post by oldfred on 2014-11-22
FAT32?
That would indicate you have UEFI? 
And you do not just click install now, but have to specify size of / (root), /home (if you have that) and swap.

If allocating that much you should have separate /home and perhaps a shared NTFS data partition. The shared NTFS cannot be made during install, but either before or after.

Did you already reboot into Windows so it can run chkdsk?
Did you already backup Windows and efi partition and make a repair flash drive?

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

And only use Something Else if reinstalling or else you will have to have all those Windows backups.

---

### Post by ray9 on 2014-11-23
I made a recovery disk.  I quit the the install because I don't know what I'm doing so I'll have to keep reading.

---

### Post by Sef on 2014-11-23
> [COLOR=#000000]I made a recovery disk. I quit the the install because I don't know what I'm doing so I'll have to keep reading.

Does the recovery back up your data?  Back it up before attempting the install.  [/COLOR]

---

