---
title: "Windows XP Boot problems"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by bobheaps on 2008-10-16
My system is/was a dual boot system, Ubuntu and windows xp and was working well. I had problems with windows and had to re-install it. I lost the option of Ubuntu at boot up time; it booted directly into windows. I have a super grub disk which I used. I got back the Ubuntu option but lost the windows one. Can someone point me to a howto file that will show me how to add windows to the options list at boot time
Thanks

---

### Post by GuitarRocker2562 on 2008-10-16
Post your /boot.grub/menu.lst file.

---

### Post by kansasnoob on 2008-10-16
Go to terminal and post the output of:

```
 sudo fdisk -l
```

That's a lower case L.

And also:

```
 cat /boot/grub/menu.lst
```

Again, that's a lower case L.

---

### Post by kansasnoob on 2008-10-17
Well, I'm soon off to bed but look here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

That last part where it says:

> Reboot the system. You'll get the GRUB bootloader but Vista **(should say XP)** won't be an option - we need to add this to the boot options.

Boot into Ubuntu and open up another Terminal session. Then, type in sudo gedit /boot/grub/menu.lst

Scroll down to the bottom of the file and type in the following text strings:

Reboot the system. You'll get the GRUB bootloader but Vista won't be an option - we need to add this to the boot options.

title Windows XP
root (hd0,1)
makeactive
chainloader +1

Save the file and reboot. When the GRUB loader launches hit ESC for the boot menu. Windows XP is the last option - select it and XP will load.

If you want to make the GRUB menu always available, boot back into Ubuntu and edit the MENU.LST file. Find the hiddenmenu text string and change it to #hiddenmenu.

To increase the menu timeout, change the default timeout 3 to something more appropriate. 

Save the file and reboot. When the GRUB loader launches hit ESC for the boot menu. Windows XP is the last option - select it and XP will load.

If you want to make the GRUB menu always available, boot back into Ubuntu and edit the MENU.LST file. Find the hiddenmenu text string and change it to #hiddenmenu.

To increase the menu timeout, change the default timeout 3 to something more appropriate. 

The reason I wanted to see your fdisk -l and menu list was to see if adding this:

> title Windows XP
root (hd0,1)
makeactive
chainloader +1

would be right. It depends on what partition XP is on, whether or not you have more than one hard drive, etc.

---

