---
title: "Grub won't load after installing 16.04 with dual boot"
date: 2016-10-10
forum: New to Ubuntu
---

### Post by panagiotisf on 2016-10-10
I have installed ubuntu 16.04 alongside windows 10, but when I restarted, grub would not load, instead i go straight to windows.
Have tried pressing Shift but still nothing.
I run boot repair from live usb and supposedly it run successfully, but still it boots into windows.
This is the boot repair results link: [http://paste2.org/enayPNch](http://paste2.org/enayPNch)

---

### Post by oldfred on 2016-10-10
What brand/model system?
Many need work arounds as they do not comply with UEFI standard that says not to use description as part of boot. And then only valid description is "Windows Boot Manager". But there are many work arounds, some better for different configurations or brands. And some brands like Acer require UEFI settings to allow other systems.

You also show Windows fast startup on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

### Post by panagiotisf on 2016-10-10
I have an acer aspire v5-591g-546p and I switched off fast start up.
I also run another boot-repair and this is the new result: [http://paste2.org/zEkVB1FH](http://paste2.org/zEkVB1FH)
Grub still wont load

---

### Post by oldfred on 2016-10-10
Acer has a unique requirement.
You have to set a supervisory password in UEFI and in UEFI drill down in ESP - efi system partition and set "trust" on the grub/ubuntu .efi boot files.

Some older threads mention that version of UEFI must be downgraded, but newer threads say newest UEFI from Acer works. So make sure you have newest UEFI from Acer.

 Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
      
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by panagiotisf on 2016-10-11
Thanks [http://ubuntuforums.org/showthread.p...2#post13369742]("http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742") solved my problem. Did not need to update bios (InsydeH20 r 5.0, v1.2 was fine)

---

