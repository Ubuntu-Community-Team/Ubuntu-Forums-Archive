---
title: "Hotplug USB for KDE"
date: 2005-02-13
forum: Programming Talk
---

### Post by cwaldbieser on 2005-02-13
I installed KDE 3.2 for my Ubuntu system, and it seemed to work fairly well, but I noticed some little things that I thought I'd try to correct.  One thing was that when I plug in my USB drive, it doesn't automount, put an icon on the desktop, or open the drive in the file manager (under GNOME, all these things happen).

I did some reading, and I added a line to my /etc/fstab so normal users could mount and use the drive.  Next I read about the hotplug system for Linux, and it seemed that all I had to do was write a .usermap file that calls a script I write that does all the heavy lifting.

I have been beating my brains out trying to get a simple script to work.  It is supposed to copy a desktop shortcut to the usb drive to my desktop when the drive is plugged in, but something is going wrong, and I am not sure exactly what.

I tried calling the /etc/hotplug/usb.agent script manually with DEBUG=yes, but all it seems to tell me is that the usb.agent script can't figure out how to load my script.

Anybody have any experience with this?  I am including my .usermap and script in case anyone wants to take a peek and let me know what's going wrong.

Thanks,
Carl Waldbieser

-------- begin /etc/hotplug/usb/flashdrive.usermap -------------------
```
flashdrive 0x0003 0x05dc 0x0080 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
```
-------- end /etc/hotplug/usb/flashdrive.usermap ---------------------

-------- begin /etc/hotplug/usb/flashdrive ---------------------------
```
#!/bin/bash
if [ "$ACTION" = "add" ]; then
	cp "/home/carl/USB Drive.desktop" /home/carl/Desktop
fi
```
---------end /etc/hotplug/usb/flashdrive ----------------------------

---

### Post by cwaldbieser on 2005-02-15
OK, I toyed around with this a bit, and I have this at least partially working.

I made the /etc/hotplug/usb.usermap script
```
flashdrive 0x0000 0x05dc 0x0080 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
```

Then I changed my script (/etc/hotplug/usb/flashdrive) to
```
#!/bin/bash

if [ "$ACTION" = "add" ]; then
    #Sleep until the device becomes available.
    while [ ! -e /dev/sdb1 ]; do
        sleep 1
    done

    #Make the mount point and mount if it does not exist.
    mkdir -p /media/sdb1
    mount /dev/sdb1

    #Create the desktop icons on each user's desktop.
    for desktop in /home/*/Desktop
    do
        cat > "$desktop/USB Drive.desktop" << DRIVEFILE
[Desktop Entry]
Dev=/dev/sdb1
Encoding=UTF-8
Icon=hdd_mount
MountPoint=/media/sdb1
ReadOnly=false
Type=FSDevice
UnmountIcon=hdd_unmount
DRIVEFILE
    done
fi
```

This creates the desktop icon when I plug the drive in.  I changed my /etc/fstab to include the users option so anyone could mount/unmount, and that seems to work OK for my purposes.

However, I have a feeling this is going to interfere with how things were working in Gnome.  Also, I have no idea how to detect when the drive is removed.  The hotplug docs seem to indicate the script will be called with ACTION=remove, but I can't seem to detect it happening.

Any ideas?

Thanks,
Carl Waldbieser

---

### Post by cwaldbieser on 2005-02-17
Addendum:

When I rebooted, I found that my startup scripts were hanging on my flashdrive script-- it was waiting for /dev/sdb1 to become available when it wasn't plugged in!

I added the following to the beginning of the script, and that seemed to take care of the problem:

```
#If the USB device is not plugged in (e.g. during bootup), then skip trying to perform an action.
if [ -z "$(lsusb | grep 05dc:0080)" ]; then 
    exit 0
fi
```

I also found that I could mv /etc/hotplug/usb.usermap /etc/hotplug/usb/flashdrive.usermap and everything still worked.

Still no luck on getting ACTION=remove to work, though.

---

### Post by pebble on 2005-02-22
[QUOTE=cwaldbieser]
Still no luck on getting ACTION=remove to work, though.[/QUOTE]

Have you seen the note at the end of this page?
[http://www.xs4all.nl/~bsamwel/usb_storage_on_debian.html](http://www.xs4all.nl/~bsamwel/usb_storage_on_debian.html)

---

### Post by cwaldbieser on 2005-02-27
Ooh!  Thanks!  I'll have to check it out.  Looks like maybe there is just a bugin the scripts.

---

### Post by landotter on 2005-03-10
you can always just run "gnome-volume-manager" under KDE and voila! ;) Run it from the alt+f2 dialog, then make sure to save your session as you exit.

You can have usb show up on the desktop by checking the "show hard drives" box in desktop configuration--pretty ugly with all the drives sitting there, or just go into konqui's sidebar and open your usb drive.

Or you can just right  click and create a device that will be mounted automatically when you plug it in.

To keep the service from opening up a nautilus window  when using it, run "gnome-control-center" and open up "removeable storage" to  adjust to your heart's desire.

---

