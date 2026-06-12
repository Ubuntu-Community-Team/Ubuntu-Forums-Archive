---
title: "[Ubuntu] Acer Travel Mate boot problem after system upgrade"
date: 2018-08-28
forum: New to Ubuntu
---

### Post by beleco on 2018-08-28
Dear Ubuntu Community,

In short: My laptop Acer Travel Mate B117 won't start after I've upgraded my system from 14.04 to 18.04.

Today my Ubuntu suggested that I upgrade it to the newest version. I decided to go for it. After the successful installation process system asked for a restart. I restarted it and since then I haven't been able to turn it properly on. While booting it says:
Failed to open \EFI\BOOT\mx64.efi - Not found
Failed to load image \EFI\BOOT\mx64.efi: Not Found
Failed to start MokManager: Not Found


I googled around and didn't come up with any solution. There was some talk about turning off safe boot but I don't seem to be able to do it. 
 I consider myself a linux newbie but in the past I had solved many problems. This one got me really frustrated because apart from switching boot order and boot modes I can't do much more. 
I ask you kindly for your help.

---

### Post by oldfred on 2018-08-29
All Acer have a unique requirment of setting "trust" from within UEFI on the .efi boot files.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

