---
title: "I messed up my Ubuntu dual boot installation. Please help."
date: 2016-09-29
forum: New to Ubuntu
---

### Post by moyer-cj on 2016-09-29
I installed Ubuntu on my Lenovo Yoga 710 but I was encountering a well known error with ACPI as documented here:
[https://ubuntuforums.org/showthread.php?t=2328462](https://ubuntuforums.org/showthread.php?t=2328462)


So, "logically", I deleted my Ubuntu partition on Windows and now when I reboot my laptop into Ubuntu it enters Grub (obviously). 
Grub gives me the following line: "Minimal BASH-like line editing Is supported..." etc. 


[I]I have already tried booting into a live USB of Ubuntu and installing Boot Repair as well as creating a live USB of Boot Repair itself. It has not successfully repaired my problem with Grub.

[/I]
I have extensively Googled my issue and I cannot resolve it. Please help.


Here is the log file from Boot Repair:
[http://paste2.org/wVLGCWs5](http://paste2.org/wVLGCWs5)

---

### Post by yancek on 2016-09-29
I'm not sure what problem you are trying to resolve.  Obviously, if you deleted the Ubuntu partition you are not going to be able to boot it as it no longer exists.  If you are trying to boot windows, you are using UEFI so you should be able to boot using a specific key, often the F8 or F12 but it might be something else.

---

### Post by moyer-cj on 2016-09-29
I'd like to remove Grub and attempt a reinstall of Ubuntu. I'm booted into Windows right now.

---

### Post by oldfred on 2016-09-30
You can just reinstall Ubuntu using Something Else install option. Choose existing / as new / (root) and if you have /home as separate partition also choose that.
New install will overwrite grub in UEFI.
I have multiple installs of Ubuntu and each new one overwrites the old UEFI entry.

You may want to house clean older UEFI entries with efibootmgr.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by colmax on 2016-10-01
if you delete a partition it needs to be formatted
hopefully it will rebuild the partition table
may show as free space
fat32 is most common fs
if memstick isn't booting after win10 anniversary try iso on dvd

---

### Post by wardle315 on 2016-10-02
> **moyer-cj said:**
> So, "logically", I deleted my Ubuntu partition on Windows and now when I reboot my laptop into Ubuntu it enters Grub (obviously). 
Grub gives me the following line: "Minimal BASH-like line editing Is supported..." etc. 

[I]I have already tried booting into a live USB of Ubuntu and installing Boot Repair as well as creating a live USB of Boot Repair itself. It has not successfully repaired my problem with Grub.

[/I]
I have extensively Googled my issue and I cannot resolve it. Please help.


Here is the log file from Boot Repair:
[http://paste2.org/wVLGCWs5](http://paste2.org/wVLGCWs5)

Boot repair won't work as there isn't any Ubuntu installation on your system to repair as you deleted the partition it was in. All you can dois use your live CD / USB to re-install Ubuntu and then when you install select the option "Install Ubuntu Alongside Windows". This should fix your dual-boot.

---

