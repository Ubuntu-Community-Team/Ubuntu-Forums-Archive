---
title: "Install grub2 on sda and sdb"
date: 2015-06-05
forum: New to Ubuntu
---

### Post by crip720 on 2015-06-05
I have a multi-boot setup, and the other day I install Win 10 on a partition.  I tried to use boot-repair from an usb install of Deepin, but Deepin did not work well.  The usb stick did have grub installed on it so I was able to get back into Ubuntu 14.04.  I installed boot-repair in Ubuntu and ran it, but it seems to have trouble installing grub on sda, it says to have bios boot from sdb.  SDA has Win7, Win10 and Ubuntu14.04 32bt.  Sdb is external usb hard drive with my main Ubuntu14.04 64bt on it.  Booting from sdb is giving me error of missing/unknown filesystem.  I would like to use "sudo grub-install /dev/sda" . I would also like to do this for sdb.  Can I do this?  I did use advance tool in boot-repair and told it to install grub on all disks with an OS.  Boot-repair paste is [http://paste.ubuntu.com/11600577/](http://paste.ubuntu.com/11600577/).  Thank you, Colin.

---

### Post by grahammechanical on 2015-06-05
It seems that Boot Repair did what you told it to do

> =================== User settings
The settings chosen by the user will reinstall the grub2 of sdb1 into the MBR of sdb.
It will also fix access to other systems (other MBRs) for the situations when the removable media is disconnected.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


You need to access at least one installation of Ubuntu. And it is not clear if you can load into the Ubuntu on sda. If you can access Ubuntu on sda, then do so and run

```
sudo grub-install /dev/sda
sudo update-grub
```

If you have the external USB drive connected when you do that you should then be able to load into Ubuntu on sdb and run

```
sudo grub-install /dev/sdb
sudo update-grub
```

Then you can use the BIOS to select which hard drive to boot from. If you cannot load into either installation of Ubuntu then load a Ubuntu live session and use the file manager to open both sda and sdb and then run those two sets of commands.

Regards.

---

### Post by crip720 on 2015-06-06
I ran both sets of code and received no errors.  Will see if it works on next boot.  I did tell boot-repair to place grub on all disks, but it did not listen to me.  Thank you.  Will mark as solve.  Colin.

---

