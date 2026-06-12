---
title: "Ubuntu is not showing in boot loader"
date: 2014-09-22
forum: New to Ubuntu
---

### Post by divay_jeet on 2014-09-22
I just installed Ubuntu 14.04(as my first Linux). after installation i restart my system and window 7 start. when i check by pressing F9, it shows only  window 7. cant understand what to do? i hav Lenovo z570 with 3GB ram and 600GB Toshiba HDD. during installation make 3 drives, these are-

21000 MB for ext 4 with "/" Logical partition sda 5
3000 MB for swap logical partition 
30000 MB drive ext 4 with " /home" logical partition sda 7

then i select "ext 7 /home " drive for boot loader installation and rest is know by everyone.
after installation it say for restart and after restart it automatically start window 7.

don't know what to do now. as i am just entered in Ubuntu community guide me. 
Thank You ):P

---

### Post by dave131 on 2014-09-22
run boot-repair (if it's not installed you can install it by opeing a terminal window [ctrl/alt/t] and type "sudo apt-get install boot-repair),but don't actually do anything.  Write down the link it shows to your information and post that back here.  BTW - do you know if your PC is set for uefi and if Windows 7 was installed in uefi (assuming this is possible - I don't know).

---

### Post by kc1di on 2014-09-22
Grub Bootloader needs to be installed in your MBR not /home partition. 
As the above poster said get a copy of boot repair and run it. it will install Grub in the mbr for you.
you can get boot repair[ here:]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by CantankRus on 2014-09-22
You need to select the drive (sda) not a partition (sda7) to install the bootloader to.
Be aware that you will need to reinstall the windows bootloader should you want to uninstall ubuntu.

Easiest fix would be to use  [**_[COLOR="#B22222"]Boot-Repair[/COLOR]_**]("https://help.ubuntu.com/community/Boot-Repair")
Also have a read here...
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

**[COLOR="#FF0000"]Make sure you have a Windows backup[/COLOR]**

---

