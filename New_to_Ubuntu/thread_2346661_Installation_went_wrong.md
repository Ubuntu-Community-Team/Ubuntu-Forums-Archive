---
title: "Installation went wrong"
date: 2016-12-17
forum: New to Ubuntu
---

### Post by flex567 on 2016-12-17
I have at least 2 partitions on my hard drive. On 1 I have linux 16.10 which I just installed over 16.04. On the other I have Windows 7. 
Until I didn't install 16.10 I was asked on boot by GRUB which OS should I run, I had 2 options Windows 7 and Ubuntu. 
Now After installing 16.10 GRUB only offers Ubuntu and not Windows 7 anymore. How can I change that so that at boot I will be asked again about which OS do I want to run?

---

### Post by Impavidus on 2016-12-17
Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Don't run the recommended repair yet, but create a BootInfo summary and post the link here. That should give us the details we need.

---

### Post by yancek on 2016-12-17
Did you update to 16.10 from 16.04 or did you do a completely new install?  Did you install Ubuntu to the same partition(s) on which you had 16.04?
The first thing you should try is to open a terminal and run this command:

```
sudo update-grub
```

Watch the output for a windows entry.  If you see one, reboot to test booting windows.  If you don't see one, go to the site below and get the boot repair software, download and run it and select the option to Create BootInfo summary and post a link to the output here.  That should give enough useful information for someone to advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by flex567 on 2016-12-17
> Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").  Don't run the recommended repair yet, but create a BootInfo summary and  post the link here. That should give us the details we need.
[http://paste2.org/LBfMUHW1](http://paste2.org/LBfMUHW1)

> Did you update to 16.10 from 16.04 or did you do a completely new  install?  Did you install Ubuntu to the same partition(s) on which you  had 16.04?
I tried to update and then something went wrong and I decided to manually install 16.10.
I think I installed it on the same partition because I can access other partiotion and all files are still there only windows is not an option at boot.

```
sudo update-grub
[sudo] password for seba: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-22-generic
Found initrd image: /boot/initrd.img-4.8.0-22-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```

---

### Post by flex567 on 2016-12-17
I think > sudo update-grub helped. thanx.

---

### Post by oldfred on 2016-12-17
Since removeable drive, best to have Windows boot loader in MBR of internal drive. Otherwise you can only boot Windows from grub menu on external.

Reinstall Windows boot loader using Boot-Repair or your Windows repair flash drive. Best to have Windows repair disk as Boot-Repair can only do minor fixes to Windows.

And set external drive as first in BIOS boot order and internal second. Then when external plugged in you will get grub menu and can choose Windows or Ubuntu. With drive unplugged then Windows will boot directly.

You showed grldr which is probably from EasyBCD which uses the old grub4dos to chain load to grub. Best to just remove that as you have two MBRs to boot from.

---

### Post by flex567 on 2016-12-17
> Since removeable drive, best to have Windows boot loader in MBR of  internal drive. Otherwise you can only boot Windows from grub menu on  external. I don't have the removable drive

---

### Post by oldfred on 2016-12-17
In Boot-Repair you ticked the removeable in report.

If not removeable, you still use same logic. But Boot-Repair will normally install grub to the MBR of all internal drives. You do not want that, so use its advanced mode and choose Ubuntu and sdb for install of boot loader. Make sure Ubuntu boots ok.
The choose Windows install and sda to install syslinux or use Windows repair disk to fixMBR to have Windows boot loader in sda. Check that from BIOS you can directly boot Windows.
Then change BIOS to boot from sdb/Ubuntu drive first and Windows drive second.
You then can normally boot Windows from grub. But grub only boots working Windows which means no hibernation nor needing chkdsk. When Winows needs that you may be able to directly boot, or may need Windows repair disk.

---

### Post by flex567 on 2016-12-17
I don't know why should I change anything because now everything works.

---

### Post by oldfred on 2016-12-17
You do not have to.

Just be sure to make a Windows repair flash drive or have the Windows install DVD or flash drive, so you can get into a repair/recovery console, if needed.
And keep the Ubuntu live installer to make repairs, again if needed.

---

