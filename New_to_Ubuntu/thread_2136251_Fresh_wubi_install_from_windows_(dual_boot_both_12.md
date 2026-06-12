---
title: "Fresh wubi install from windows (dual boot both 12.04 and win7) NO mouse NO keyboard"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by awesnap on 2013-04-17
Hello all.

I haven't tried ubuntu for some time, and want to see whats good with 12.04.  When I did a fresh install (From wubi) I restarted, and booted into ubuntu.  Got to the opening splash screen asking me for my password, but no mouse and no keyboard control.  I have 2 sets, one is a logitech wireless all in one, and the other is a single usb mouse and a single usb keyboard.  I even have a usb to PS2 adapter that I stuck in the PS2 receiver, but no luck.  I have no other linux distros installed anywhere, can someone help me get past this first step?

Thanks a LOT in advance!

---

### Post by oldfred on 2013-04-17
Added wubi to your title. Only a few here know wubi and I am not one of them.

I do have a Logitech wireless mouse with my full install on 12.04 and it just works on my laptop. Years ago I had issues with my desktop and had to go into BIOS and turn on USB keyboard & mouse support. But both Windows & Ubuntu worked, it was just grub menu that did not work. With wubi you do not really boot with grub as it uses the Windows boot loader.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

      
 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

---

### Post by bcbc on 2013-04-17
This has nothing to do with Wubi... more likely some hardware incompatibility. Maybe even graphics. Use nomodeset if you have a radeon or nvidia card.

Otherwise if not the case, full brand/model/graphics/.. other hardware will help figure out the problem.

---

