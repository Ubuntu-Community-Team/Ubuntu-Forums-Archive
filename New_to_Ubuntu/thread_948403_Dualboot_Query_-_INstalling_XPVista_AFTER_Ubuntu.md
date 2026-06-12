---
title: "Dualboot Query - INstalling XP/Vista AFTER Ubuntu"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-15
Hey, already have Ubuntu installed, and i have some spare partitions already made.

WMP9 won't work under wine (need it to get sound for a game) so looks like i'm gonn have to installed el richmond produce again.

IS there anything i need to do/be aware of in not deleting my GRUB/MBR when installing vista and/or xp?

---

### Post by perlluver on 2008-10-15
You could run Windows in a virtual machine, or you can have a look at this: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm), just be careful, when doing this, and backup your data.

---

### Post by kansasnoob on 2008-10-15
For XP:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

For Vista:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by joey-elijah on 2008-10-15
well i already have XP in a virtuabox (which has now broken after the kernel update and despire compiling the new modules/using synpatic to install relevant modules) won't work hence needing/wanting to install Vista again.

HOwever, ubuntu is (obviosuly) already installed, and whislt those guides are fine, through my searching on the 'net, i can't seem to find out how you install Vista on a SEPARATE harddrive with Ubuntu already installed. The setip just tells me it's the UBuntu harddrive it wants, or it won't install.

---

### Post by falkTX on 2008-10-15
You can try this: (you'll need to understand a little of hardware)

1. Remove the Ubuntu disk, and set the one for Vista/XP as "Master"
2. Install Windows normally
3. Insert the Ubuntu disk as Master and the Vista/XP as slave
4. Boot Ubuntu and run:
"sudo update-grub /dev/sda" (modify anything if needed)

You should have now dual-boot Linux and Windows

---

### Post by lukjad on 2008-10-15
Try this link:
[http://thevistaforums.com/index.php?showtopic=19902](http://thevistaforums.com/index.php?showtopic=19902)

---

### Post by joey-elijah on 2008-10-15
> **lukjad007 said:**
> Try this link:
[http://thevistaforums.com/index.php?showtopic=19902](http://thevistaforums.com/index.php?showtopic=19902)

already tried those links thanks, but they're not applicable as i have ubuntu on it's own harddrive and don't want to share it with windows.

Geesh. All this just so i can play a game!

thanks falkTX, will try that.

---

### Post by falkTX on 2008-11-10
Did it worked?

---

### Post by lukjad on 2008-11-10
I think he just quit.

---

