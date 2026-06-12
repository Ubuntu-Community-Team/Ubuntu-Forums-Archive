---
title: "Boot Repair - Windows 7 want to dual boot Ubuntu 14 then Grub not displayed."
date: 2015-09-28
forum: New to Ubuntu
---

### Post by Raabb_Ajam on 2015-09-28
Hello,

[boot-repair link] [http://paste.ubuntu.com/12600591/](http://paste.ubuntu.com/12600591/)

I have a new notebook pre-installed with Windows 7. 
I tried to dual-boot with Ubuntu 14.04. 
After installing Ubuntu using Unetbootin smoothly and then rebooting, the menu to select which OS to boot is still not showing. 
I use Boot Repair and followed the recommended installation.
It also work smoothly without error.
After reboot it still not showing the OS selection menu.
I look into the BIOS boot order, and the order is USB > CD > HD, I don't see other options like reserved boot volume.
I try to change the Windows bootloader using `[COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#000000]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#000000]himx64.efi` but still nothing changes.

What should I do? 
I have installed Ubuntu before without dual boot and just overwrite old OS, that seems a lot easier, should I just do that? 
But my HP laptop is pre-installed with Windows 7 and it has a lot HP assistant programs, Nvidia program, I am afraid it will be more hassle in the long run if I removed the Windows 7.
Also, I prefer to dual boot if it is possible.

Thank you.

---------------------- Edit [/COLOR][COLOR=#000000]----------------------
[/COLOR][COLOR=#000000]After some more reboots, I notice there is an option to choose boot device on reboot by pressing 'esc' key first and then F9, which is different from BIOS settings F10.
Now I can access my installed Ubuntu by choosing Ubuntu on boot device.
It works smoothly.
But the default boot when I don't press esc and F9 key will always Windows 7.

I want the old grub way, where the default is displaying menu to choose OS to boot. Please give me some suggestions.

Thank you.

[/COLOR]

---

### Post by oldfred on 2015-09-28
Your Windows is installed in UEFI boot mode as is Ubuntu.
And Windows 7 does not support UEFI secure boot nor use the newer Windows fast start up, so those should not be issues.

Can you in UEFI just select ubuntu as first boot option?, Windows second and all others later in boot order?

You may also from efibootmgr change boot order.
       Change boot order with efibootmgr, some require all 4 char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

check order
sudo efibootmgr -v

 sudo efibootmgr -o 4,3

      
 [URL="http://linux.die.net/man/8/efibootmgr"]http://linux.die.net/man/8/efibootmgr
[/URL]
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

[URL="http://linux.die.net/man/8/efibootmgr"]
[/URL]

---

