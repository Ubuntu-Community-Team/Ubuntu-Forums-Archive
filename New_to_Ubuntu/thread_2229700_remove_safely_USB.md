---
title: "remove safely USB"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by hill0093 on 2014-06-14
I just downloaded and installed Ubuntu on my 17-nch HP laptop.
I inserted some Windows 7 files using a USB flash drive.
.mp4 and .mp3's play.
I didn't see a way to safely remove the USB drive.
When I put the drive back into the W7 computer it wanted to check for errors.
How do I safely remove the USB drive like in Windows 7 ?

---

### Post by Dennis N on 2014-06-14
In Ubuntu (Unity), an icon for the USB drive will show up on the Unity Launcher at the bottom end when it is inserted. Right click on the icon and there should be an option to safely remove the drive in the menu that appears.

---

### Post by ajgreeny on 2014-06-14
The drive will also show in whatever file manager you use (nautilus in Ubuntu) where you can right click and choose either **Unmount** or **Eject**

---

### Post by kurt18947 on 2014-06-14
> **ajgreeny said:**
> The drive will also show in whatever file manager you use (nautilus in Ubuntu) where you can right click and choose either **Unmount** or **Eject**

Like that.  Some desktops - I'm not sure about Unity - can also be set to show removable storage devices on the desktop.  In that case, right-click usually offers an 'unmount' or 'safetly remove' option.

---

### Post by gaxfax on 2014-06-14
Try these instructions

[http://stackoverflow.com/questions/13224509/linux-ubuntu-safely-remove-usb-flash-disk-via-command-line](http://stackoverflow.com/questions/13224509/linux-ubuntu-safely-remove-usb-flash-disk-via-command-line)

You can do this using udisks. it is not installed by default but easy  enough to install (the package is like a meg in size once installed)...
  sudo apt-get install udisks
  Once installed you can detach a USB drive with the following commands...
  sudo udisks --unmount /dev/sdb1
sudo udisks --detach /dev/sdb

---

### Post by Odyssey1942 on 2014-06-15
So what is the difference between unmount, eject, and safely remove drive?

---

### Post by Dennis N on 2014-06-15
> **Odyssey1942 said:**
> So what is the difference between unmount, eject, and safely remove drive?

As to eject and safely remove, the only difference I notice is that eject gives a notification that the device has been ejected. Safely remove gives no notification at all. Otherwise, the result appears to be the same. In both cases, the icon disappears, and to reaccess that USB, you have to physically remove it and replug (If there are real differences, I'm sure someone will point out what they are).   

Neither Lubuntu nor Xubuntu have a Safely Remove option. They have Eject and Unmount options. With Unmount, the icon remains, and you can remount and open it again with a right click - no need to reinsert. Ubuntu 12.04 has no unmount option in the right-click menu.

Comments based on Ubuntu 12.04, not later versions, which could have different behavior and options.

---

### Post by ajgreeny on 2014-06-15
I'm not sure about the "Safely remove" option as I don't think I've ever seen that in a Linux context, only in my (now gone) WinXP.

However one of the differences between **unmount** and **eject** seems to be the amount, or degree of removal of the USB from the system.  If you **eject** a USB but leave it plugged in then run **sudo fdisk -l** you will see that the USB is not detected by the system; it will not show in gparted either.  If you merely **unmount** the USB then run the fdisk command again or run gparted you will see that the USB is still detected.

---

### Post by Dennis N on 2014-06-15
> I'm not sure about the "Safely remove" option as I don't think I've ever seen that in a Linux context, only in my (now gone) WinXP.

Possibly the "Safely Remove" option was put in Ubuntu as a reassuring choice for new users from Windows.

---

### Post by Odyssey1942 on 2014-06-16
Could it possibly have to do with closing files. The caution on removing USB devices is that open files may be corrupted, especially if being written to. 

Eject might just be the equivalent of unplugging the device, whereas unmount might be a bit more file sensitive.

Safely remove certainly implies that files are being closed properly.

Just outright guessing here. Hopefully someone who knows the actual info will enlighten us.

---

### Post by Dennis N on 2014-06-16
> Could it possibly have to do with closing files. The caution on removing USB devices is that open files may be corrupted, especially if being written to. 
I think so. I consider "eject" to be equivalent to "safely remove", and have used both eject and safely remove in Ubuntu over the years with no problems from eject. It is safe. In Lubuntu and Xubuntu eject is the menu option to use if you plan to unplug the USB since there is no "safely remove".

---

### Post by hill0093 on 2014-07-02
> **Dennis N said:**
> In Ubuntu (Unity), an icon for the USB drive will show up on the Unity Launcher at the bottom end when it is inserted. Right click on the icon and there should be an option to safely remove the drive in the menu that appears.
Evidently, "eject" is that safely remove option.

---

### Post by mc4man on 2014-07-02
In practice both eject & safely remove are about the same but safely remove also powers off the device(port
In recent nautilus versions the option to unmount a removable device has been removed.

As far as usb flash drives the available options depend on the device itself - 
Some  only get eject, some only safely remove, some both eject & safely remove.

As far as windows complaining about a flash drive that's had various files added in Ubuntu - I see that all the time, I just ignore/dismiss the windows dialog.

---

### Post by 3rdalbum on 2014-07-03
> **mc4man said:**
> In practice both eject & safely remove are about the same but safely remove also powers off the device.

+1.

---

### Post by stalkingwolf on 2014-07-03
I prefer the safely remove option so before i install i make sure it is available.  Thats just my preference.  One note i will make is , make sure the activity light stays off before
removing the drive.  I have had drives that remount within a few seconds after using safely remove. It will also tell you if something is still active , say you minimized a file instead of closing it or a copy process is still active.

---

