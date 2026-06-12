---
title: "Hard drive issue..."
date: 2013-01-22
forum: New to Ubuntu
---

### Post by soundwave1236 on 2013-01-22
okay ubuntu noob here im using the latest version of ubuntu im using the bootable usb stick i also have an external hard drive plugged in aswell im trying to download and save games but it wont says i dont have enough space its a 320gb hard drive any help would be appreciated.

---

### Post by audiomick on 2013-01-22
It is probably trying to save to the USB stick you are booted to. You need to direct the save process to a directory on the hard drive.

---

### Post by soundwave1236 on 2013-01-22
> **audiomick said:**
> It is probably trying to save to the USB stick you are booted to. You need to direct the save process to a directory on the hard drive.
how do i do that?should i just make the hard drive bootable instead?

---

### Post by audiomick on 2013-01-22
I think you should be able to right click on the link to the file you want, and then choose a destination in the window that appears.

You might possibly have to access the drive with the file manager first, i.e. open the file manager and navigate to the directory on the drive, to get it mounted.  The drive should be visible as an icon in the left panel of the file manager.

You can mount via the terminal, of course, but I don't know the exact command off hand.

---

### Post by Cheesemill on 2013-01-22
What exactly do you mean by 'trying to download and save games' ?

If you are using the Software Centre to try and install games then you are probably out of luck. Applications installed using the Software Centre have to go on the same drive that Ubuntu is installed onto.

If you are downloading files using a web browser then you can right-click on the link and select Save As... and then select your external drive as the download location.

---

### Post by audiomick on 2013-01-22
> **audiomick said:**
> 
You might possibly have to access the drive with the file manager first, i.e. open the file manager and navigate to the directory on the drive, to get it mounted.  The drive should be visible as an icon in the left panel of the file manager.

You can mount via the terminal, of course, but I don't know the exact command off hand.

As I said, you should be able to see the drive in the left pane of the file manager and click on it to mount.

The command from the terminal is mount. Look at 
```
man mount
```

for an explanation of the various options. I haven't used this at all, so I'm not much help there, but I know it is the right command.

If you are not sure whether the computer is seeing the drive at all, try having a look with gparted. If you are booted into a live environment as your first post indicates, that should be installed.

---

