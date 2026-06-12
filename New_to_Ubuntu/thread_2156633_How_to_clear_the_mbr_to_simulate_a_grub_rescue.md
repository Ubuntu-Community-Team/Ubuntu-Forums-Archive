---
title: "How to clear the mbr to simulate a grub rescue?"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by ubunet on 2013-06-22
Hi,

I have Xubuntu 13.04 installed and I need to simulate how to recovery grub. How I delete only grub to recovery with liveUSB for demonstration?

---

### Post by fantab on 2013-06-22
Uninstalling Grub should do it for you. Or you can corrupt the boot process by deleting either /etc/boot or /etc/default/grub or /etc/grub.d/...  and then you can re-install grub using LiveDVD/USB.

---

### Post by ubunet on 2013-06-22
Did is safe execute the command below to clear the mbr?
```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

Ref.: [http://www.cyberciti.biz/faq/linux-clearing-out-master-boot-record-dd-command/](http://www.cyberciti.biz/faq/linux-clearing-out-master-boot-record-dd-command/)

---

### Post by oldfred on 2013-06-22
I hesitate to suggest dd as any typo will cause damage. 
 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)



 Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master](https://help.ubuntu.com/community/WindowsDualBoot#Master) Boot Record backup and re-replacement
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1
Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.
dd if=/dev/zero of=/dev/sda bs=446 count=1
Erase - Make double sure you have correct drive & partition
Display:
sudo dd if=/dev/sda bs=512 count=1 | hexdump -C
Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

---

