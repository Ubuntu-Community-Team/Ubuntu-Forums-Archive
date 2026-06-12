---
title: "Dual boot, Windows 8.1"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by Sean_McLeish on 2014-10-15
Hey guys,
im studying since 2 days and to complete my homework I have to use Ubuntu. I did everything and I still get this message. Could you help me please? :/
Thank you!

Windows 8.1 - trying to install Ubuntu, after that: boot-repair


[http://paste.ubuntu.com/8566281/](http://paste.ubuntu.com/8566281/)

---

### Post by mastablasta on 2014-10-16
what is the error? you can't boot?

did you : > Please do not forget to make your BIOS boot on sdb (1000GB) disk!

do you use secure boot on Windows 8?

otherwise this is the key resource: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I don't know what you assignment is but you could install in virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox) 
I would choose a lighter version like Xubuntu to do that.

---

### Post by oldfred on 2014-10-16
I do not see anything wrong.

Some brands/models only want to boot Windows by default. You may be able to boot using one time boot key, often f12 or f10 but varies by brand.
Some then require work arounds to directly boot Ubuntu.

Some Intel chips need video settings in grub menu to set correct video X by Y mode. Add setting one by one like adding nomodeset to see if one works. See other examples by ubfan1's suggestions.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Since you have Ubuntu on sdb, it often is better to configure that drive to boot without sda. But Ubuntu's efi boot is in the efi partition on sda. Difficult to reconfigure now, but in future better to have an efi partition on every drive or device.

---

