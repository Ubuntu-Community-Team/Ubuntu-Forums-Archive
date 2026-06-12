---
title: "Windows 8 on Acer laptop, can't dual boot Win 8 / Ubuntu"
date: 2017-03-19
forum: New to Ubuntu
---

### Post by frascud on 2017-03-19
Hi everyone. Hope this is the right forum.
I installed Ubuntu 14.04.3 LTS on my Acer Aspire E15 Start laptop which came with preinstalled Windows 8 on it, but i can only access to windows.
I tried with Grub2Win but it doesn't let me see the "choose operating system" menu when booting. Neither does it allow me to modify the "secure boot" option on the boot settings (everything is greyed out and I can't even set supervisor password as suggested in many sites that I checked online, so I can't disable windows's secure boot thing).
Only way to boot Ubuntu is to press F12 when starting the computer. I also tried boot-repair with recommended repair but it didn't seem to help. This is the URL given by bootrepair [http://paste.ubuntu.com/24207350/](http://paste.ubuntu.com/24207350/). I hope someone can help. Thanks
Francesco

---

### Post by Karolina.K on 2017-03-22
Have you tried this? it worked for me when i had a similar situation, [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by oldfred on 2017-03-22
Not familar with grub2win.

With all Acer in UEFI mode, you need to set a supervisory password in UEFI (never lose it, or delete when configured) and enable "trust" from inside UEFI for .efi boot files in the ESP - efi system partition.
Also make sure you have newest UEFI from Acer. 
Some threads mention downgrading UEFI, but newer ones mention newest UEFI from Acer works.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

       
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

