---
title: "Grub"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by Zeyo on 2013-02-28
So... I wanted to remove Linux (Ubuntu 12.10) from my HDD. I used gparted program that comes with Ubuntu on the CD (I burned the .iso file, back when I had Win7).
I succeded in formatting partitions (it says now unallocated). But that is not a problem... The problem is the damn GRUB... So... How do I remove tha

---

### Post by oldfred on 2013-02-28
Do you want Windows boot loader back? You then can use your Windows repairCD.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)


 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Zeyo on 2013-02-28
Yes, I want my Windows boot loader back... However, I only have Windows 7 installation disk (not repair one).

I tried that Boot repair too, but I can't see advanced options anywhere... I only see About, Quit and "Create a bootinfo summary".

---

### Post by presence1960 on 2013-02-28
Boot the Ubuntu Live CD/USB to desktop. Open a terminal and run ```
 sudo apt-get install lilo
```
ignore the warnings and continue. Once installed run in terminal ```
sudo lilo -M /dev/sda mbr
```
where sda is the first hard disk or if you have only one disk. If windows is on a disk other than the first one adjust sda to sdb, sdc or whatever the case may be. This will put a generic windows on your MBR. Reboot without Live CD/USB and you should boot right to windows. For now assuming you have only a single disk. If multiple disks post back for clarification.

For future reference : when removing linux you have to fix the MBR. It is easier to do it from the ubuntu installation prior to removing ubuntu since you don't have to boot a Live CD/USB nor boot a windows CD/DVD. This method works for XP, Vista, 7 and 8.

---

### Post by Zeyo on 2013-02-28
tried that... Got a message when I put in my Win7 installation disc:
```
No partition active

Reboot and Select proper boot device
or Insert boot Media in selected Boot device and press a key
```

Maybe I forgot to mention that I didn't have any other OS than Linux when I attempted to delete it...

---

### Post by presence1960 on 2013-02-28
> **Zeyo said:**
> tried that... Got a message when I put in my Win7 installation disc:
```
No partition active

Reboot and Select proper boot device
or Insert boot Media in selected Boot device and press a key
```

Maybe I forgot to mention that I didn't have any other OS than Linux when I attempted to delete it...

Yes MAYBE you did. If you had no other OS when you deleted Ubuntu you should now boot from the Windows installation CD/DVD/USB media and install windows. You have to select to boot from the CD/DVD drive by depressing a key which will give you boot options. On my machine it is F9. Otherwise it will try booting from the hard disk and that is why you are getting that error message. What is make and model of your machine?

---

### Post by presence1960 on 2013-02-28
Or go into BIOS (Setup) and set the CD/DVD drive as first device to boot in the Device Boot order. Save Changes and exit. When a bootable CD/DVD is in the drive at boot it will boot off that. You can then install Windows. If you still can't figure it out post back the make and model of your computer.

I hope you backed up all your data!!!

---

