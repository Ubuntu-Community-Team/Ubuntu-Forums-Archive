---
title: "Installed Ubuntu, it won't boot, and neither will Windows."
date: 2011-11-03
forum: New to Ubuntu
---

### Post by TheLiquidPlumber on 2011-11-03
OK here goes. I installed Ubuntu on my computer through the installation CD alongside my current system that ran Windows XP. I have two hard drives, one 500GB drive split into two partitions, one of which holds XP, and a freshly formatted NTFS partition that formerly held Windows 7. I also have an old 30GB drive which I chose to install Ubuntu on. I ran through the steps of the installation, and everything seemed fine. But when it rebooted after installing, I got an error message from my monitor telling me that the resolution  was set to 7000x6000 and that it didn't support that resolution. I disconnected my hard drives, reconnected them, and rebooted. After that, there weren't any monitor errors, but now when I try to boot from my windows hard drive, it shows a black screen with a text input cursor (not a mouse cursor, the flickering one shown when typing) and does nothing. It does boot from my install cd, so the problem must have something to do with the hard drives. Please help, I need a usable system.

---

### Post by fantab on 2011-11-03
> **TheLiquidPlumber said:**
> OK here goes. I installed Ubuntu on my computer through the installation CD alongside my current system that ran Windows XP. **I have two hard drives, one 500GB drive split into two partitions, one of which holds XP**, and a freshly formatted NTFS partition that formerly held Windows 7. **I also have an old 30GB drive which I chose to install Ubuntu on**. I ran through the steps of the installation, and everything seemed fine. But when it rebooted after installing, I got an error message from my monitor telling me that the resolution  was set to 7000x6000 and that it didn't support that resolution. I disconnected my hard drives, reconnected them, and rebooted. After that, there weren't any monitor errors, but now when I try to boot from my windows hard drive, it shows a black screen with a text input cursor (not a mouse cursor, the flickering one shown when typing) and does nothing. It does boot from my install cd, so the problem must have something to do with the hard drives. Please help, I need a usable system.

So you have two HardDrives , /dev/sda (500gb) and /dev/sdb (30gb). On which HardDrive did you install your GRUB?

If you have installed your grub on /dev/sdb then did you **change the boot order in the BIOS** to boot /dev/sdb first? because presently it is booting /dev/sda first.

Check these and get back/

---

### Post by TheLiquidPlumber on 2011-11-03
> **fantab said:**
> So you have two HardDrives , /dev/sda (500gb) and /dev/sdb (30gb). On which HardDrive did you install your GRUB?

If you have installed your grub on /dev/sdb then did you **change the boot order in the BIOS** to boot /dev/sdb first? because presently it is booting /dev/sda first.

Check these and get back/

Gosh I'm clueless... How would i go about doing that?


Note that I've never used Ubuntu or any form of Linux.

---

### Post by oldfred on 2011-11-04
Just so we know where everything is at, from your liveCD you used to install, download and run this script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

You can also download this repair tool that will also run script and may make minor repairs. It also has a full download of a liveCD.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by doctorbighands on 2011-11-04
+1 for Boot Repair. I've used it a half dozen times in the last 48 hours alone, and it's like magic. Works every time. Just boot any Ubuntu Live CD and follow the instructions on the page oldfred referenced ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).

---

### Post by TheLiquidPlumber on 2011-11-04
> **doctorbighands said:**
> +1 for Boot Repair. I've used it a half dozen times in the last 48 hours alone, and it's like magic. Works every time. Just boot any Ubuntu Live CD and follow the instructions on the page oldfred referenced ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).


OK, what exactly is [pastenbt] and [gawk], and why do I need them to make a boot info summary?

---

### Post by TheLiquidPlumber on 2011-11-04
> **TheLiquidPlumber said:**
> OK, what exactly is [pastenbt] and [gawk], and why do I need them to make a boot info summary?

Never mind that now. I used boot repair, and all is well. Thanks for the quick help!

---

