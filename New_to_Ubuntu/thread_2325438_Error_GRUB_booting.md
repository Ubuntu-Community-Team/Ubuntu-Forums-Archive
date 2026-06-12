---
title: "Error GRUB booting"
date: 2016-05-22
forum: New to Ubuntu
---

### Post by Hartanto_Ario_Widj on 2016-05-22
Hi,
I just install Ubuntu 16 dual boot on my Win 10 PC.
At the first go, GRUB won't start.
After searching around the forum, I decided to use boot-repair from my live USB.
Log : [http://pastebin.com/LVg0AJzB]("http://pastebin.com/LVg0AJzB")
Then I rebooted the PC.
At the first go, GRUB started normally. So I boot into Windows Boot Manager to check that everything is fine.
Then I rebooted the PC but since then I get the error of
"Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key"
I don't know how to boot back into Windows or even the Ubuntu on the partition /sda8
Can you help me?
Thank you in advance.

---

### Post by oldfred on 2016-05-22
I believe Toshiba has become like HP & Sony in modifying UEFI to only boot by Description and only description is "Windows Boot Manager". That is not allowed per UEFI spec.

If you use one time boot key like f112 can you choose the Ubuntu entry and boot into grub menu?
Script shows this, but there was no Windows entry? Post it again if you can boot or from live installer.

sudo efibootmgr -v

In Boot-Repair run this:
'Use the standard EFI file'
[https://bugs.launchpad.net/ubuntu/+bug/1531178](https://bugs.launchpad.net/ubuntu/+bug/1531178)

And see if a hard drive boot entry or entry that boots the fallback entry of /EFI/Boot/bootx64.efi works.

       Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

Other Toshiba and fixes they used.

 Toshiba Satellite - turned Secure boot off in Boot-Repair update
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
Toshiba Satellite C55-C5241  Windows vs. Ubuntu
[http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1)
Toshiba L50-A-1EH laptop - used bcd edit
[http://ubuntuforums.org/showthread.php?t=2295628](http://ubuntuforums.org/showthread.php?t=2295628)
Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

---

### Post by Hartanto_Ario_Widj on 2016-05-22
Thank you oldfred! I follow your instruction in [http://ubuntuforums.org/showthread.php?t=2267408]("http://ubuntuforums.org/showthread.php?t=2267408") and it works!

---

