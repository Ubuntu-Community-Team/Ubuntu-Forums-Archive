---
title: "Can't boot with GRUB on Acer machine with Windows 10"
date: 2017-07-07
forum: New to Ubuntu
---

### Post by markazhang on 2017-07-07
Hi, total beginner here.

I'm trying to dual-boot Ubuntu 16.04.2 LTS on my Acer Aspire E5 with Windows 10. I finished installing Ubuntu, but cannot get GRUB to show up when restarting my machine. So far, I have not successfully booted my installed version of Ubuntu, only the temporary "Try Ubuntu" one from my USB.

I followed these instructions: [http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

Using EasyUEFI on Windows, I saw that Ubuntu and Windows were both in the list of boot options. I disabled Windows Boot Manager to see what would happen, and upon restarting my computer, I got the message: "Default boot device missing or boot failed". In the boot manager, there was no option to boot with Ubuntu or GRUB. (I was able to undo this after booting from the USB)

I also went into the UEFI Firmwire settings and disabled "Secure Boot". I also looked at the "Boot priority order", and I didn't see any entry that said "Ubuntu." The top ones were "Windows Boot Manager", "HDD0", "HDD1".

I ran Ubuntu's "boot-repair". Here is a pastebin with the output: [[COLOR=#1155CC][FONT=Arial]http://paste.ubuntu.com/25039824/[/FONT][/COLOR]]("http://paste.ubuntu.com/25039824/")

When I restart, it still goes straight to Windows. It looks like GRUB isn't being recognized by UEFI for some reason? Any help is greatly appreciated!

---

### Post by oldfred on 2017-07-07
You need to set a supervisory password and enable "trust" on the .efi boot files from inside UEFI.
This is unique to Acer, but much better than some of the work arounds required for those that only want to boot Windows.
Also make sure you have newest UEFI from Acer. Some older Acer threads suggested downgrading UEFI, but newer threads say newest UEFI works.
       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
            Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
            Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by markazhang on 2017-07-07
Enabling "trust" on the .efi file worked perfectly. Thank you!!! :D:grin::grin:

For others reading, I followed step 35 here: [https://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](https://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

I had to turn "Secure Boot" back on as well, otherwise the option "Select an UEFI file as trusted for executing" was disabled.

---

