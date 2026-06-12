---
title: "external hard drive"
date: 2019-03-06
forum: New to Ubuntu
---

### Post by 324975kjsfghkjsf on 2019-03-06
A usb ntfs external hdd is not recognized.  It works on other computers.  It does not show up on lsusb os fstab -l.

dmesg | tail -n 20
shows:

[  158.212017] usb 1-3: new high-speed USB device number 6 using xhci_hcd
[  158.340564] usb 1-3: device descriptor read/64, error -71
[  451.466553] JFS: nTxBlock = 8192, nTxLock = 65536
[  451.500634] SGI XFS with ACLs, security attributes, realtime, no debug enabled


I installed usbmount, exfat and ntfs support.

I don't know what else to try. thanks.

---

### Post by yancek on 2019-03-06
> A usb ntfs external hdd is not recognized.  It works on other computers.  It does not show up on lsusb os fstab -l.

Does it show in the BIOS on the computer in question?  You could try booting windows since it is a windows filesystem and run chkdsk on the drive partitions.  Does it show up under the /media directory when it is attached and you are booted into Ubuntu?

---

### Post by oldfred on 2019-03-07
Are the other computers that it works in Windows?
And then do those Windows have fast start up or always on hibernation set. That sets a hibernation flag and the Linux NTFS driver will not mount it read/write or default mount to prevent damage to hibernated file system.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

