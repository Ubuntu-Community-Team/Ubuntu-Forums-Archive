---
title: "Having trouble installing ubuntu 16.04.02 on my Acer Aspire laptop"
date: 2017-07-11
forum: New to Ubuntu
---

### Post by aine9259 on 2017-07-11
I wanted to make my laptop a dedicated ubuntu computer and cannot get it to read the dvd or usb as an install disk.  There are times that it will bring up the menu that asks what you would like to do and then it "hangs" there and will go no further.  I have an Acer Aspire F5-5711-569T laptop with Windows 10 on it.  I have tried reinstalling Windows and then deleting the partitions without going further.  I have disabled the uefi and set it for legacy boot-up.  I am just not sure what else to try.  I had no problem creating a dual boot on my desktop with Windows 10 using the usb.  I am a newbie to ubuntu.

Any ideas?

Thank you  :confused::confused:

---

### Post by oldfred on 2017-07-11
While you should be able to use Legacy/BIOS/CSM, probably better to use UEFI.
But Acer has a unique UEFI requirement that requires you to enable a UEFI supervisory password and set "trust" on the grub/Ubuntu .efi boot files.
You also need to make sure UEFI is newest from Acer. Some older threads mention downgrading UEFI, but newer ones say newest Acer UEFI works.

       Acer Aspire R5-417T
[https://ubuntuforums.org/showthread.php?t=2346815](https://ubuntuforums.org/showthread.php?t=2346815)
Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 

[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

