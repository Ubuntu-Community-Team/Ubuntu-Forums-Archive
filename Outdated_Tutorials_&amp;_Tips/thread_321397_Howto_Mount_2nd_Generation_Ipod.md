---
title: "Howto Mount 2nd Generation Ipod"
date: 2006-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by madcow72 on 2006-12-18
**Updating 3/1/07:**  Found [this bug report]("https://launchpad.net/ubuntu/+source/hal/+bug/66068") dealing with the same issue about 2nd Generation Ipods not mounting properly.  I would use the following fix preferentially to the 2nd fix.  This howto is for 2nd Generation ipod Nano's, where the vFAT partition is recognized as a RAID device.  FIX 1 below is the best fix for this situation.  FIX 2 could probably be used as a more general fix, even for different ipod versions.

**[SIZE="4"]FIX 1:[/SIZE]**
Martin Jürgens at Launchpad wrote and put together the .deb files which will fix the problem with HAL not recognizing the device correctly.  There are 7 .deb files, they may be found and downloaded from [here.]("http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/")  (Although there are other files in this directory, all you need are the .deb files (7X).)

Download all deb's, place them into a folder on your desktop, let's call it "deb".  First, get the dependencies: (I think these are all the dependencies...)

```
sudo aptitude install python-glade2 python-launchpad-integration hwdb-client-gnome libdbus-1-dev libhal-storage1 libhal-dev
```

Then do the following:

```
cd /home/[COLOR="Blue"]user[/COLOR]/Desktop/deb/
sudo dpkg -i *.deb
```
(Where [COLOR="Blue"]user[/COLOR] is obviously your user name) And you should be home free.  You will probably want to reboot before everything works correctly, but this has been shown to work beautifully.

[SIZE="4"]**FIX 2:**[/SIZE]  (This is my original howto - but I'd try the fix above first.)

This is my first howto, so try to cut me some slack if I say something stupid.  However, I just spent the last few hours doing some remote administration to my brother's computer ([[COLOR="Blue"]This[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=299489") is a wonderful howto for reverse VNC which works beautifully!) and got his 2nd generation ipod to mount statically.  I have seen many posts on this subject, without a firm solution, (other than dmesg and manually mounting to a dynamic node), so I hope this helps somebody!  Most of this tutorial is ripped exactly from [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=168221"), but is tailored a little for the ipod.  This howto is meant for 2nd generation ipods.

This isn't difficult, but will require a little bit of time in a console.  I'm using kate as the editor, but if you're using the Gnome desktop, replace "kate" everywhere with "gedit".

1)  Plug in the ipod.  Then:
```
dmesg | tail -32
```
This will give you something like:
```
[SIZE="1"][17185396.732000] scsi2 : SCSI emulation for USB Mass Storage devices
[17185396.732000] usb-storage: device found at 4
[17185396.732000] usb-storage: waiting for device to settle before scanning
[17185401.732000] usb-storage: device scan complete
[17185401.736000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17185401.736000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17185401.736000] SCSI device sda: 3964928 2048-byte hdwr sectors (8120 MB)
[17185401.740000] **sda**: Write Protect is off
[17185401.740000] **sda**: Mode Sense: 68 00 00 08
[17185401.740000] **sda**: assuming drive cache: write through
[17185401.740000] SCSI device sda: 3964928 2048-byte hdwr sectors (8120 MB)
[17185401.740000] **sda**: Write Protect is off
[17185401.740000] **sda**: Mode Sense: 68 00 00 08
[17185401.740000] **sda**: assuming drive cache: write through
[17185401.740000]  **sda**: sda1 **sda2**[/SIZE]
```
What you want to know is which device node, (bold face above - **sda** for my ipod) is assigned to your ipod when it connected.

Now, you want to get some unique information about your ipod, which will allow you to assign a persistent node:
```
udevinfo -a -p $(udevinfo -q path -n /dev/**sda**)
```  (Replace **sda** with the node you got from the above command.)
This will give a lot of information, you are looking for the part that looks like:
```
  looking at device '/devices/pci0000:00/0000:00:1d.7/usb4/4-6':
    ID=="4-6"
    BUS=="**[COLOR="Red"]usb[/COLOR]**"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="000A2700187C6074"
    SYSFS{product}=="**[COLOR="Red"]iPod[/COLOR]**"
    SYSFS{manufacturer}=="Apple"
    SYSFS{maxchild}=="0"
    SYSFS{version}==" 2.00"
    SYSFS{devnum}=="4"
    SYSFS{speed}=="480"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="2"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bcdDevice}=="0001"
    SYSFS{idProduct}=="1260"
    SYSFS{idVendor}=="05ac"
    SYSFS{bMaxPower}=="500mA"
    SYSFS{bmAttributes}=="c0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

```
You only need the bold-faced, red information above.  I imagine that this information is the same for every user of a 2nd gen ipod, but just in case it's not...there it is.

The next step is to create the udev rule concerning this device.  You will create this file using:
```
sudo kate /etc/udev/rules.d/10-local.rules
```
Using the number 10 allows this to be looked at before other rules in this same folder.  You will now create the rule for your ipod, which should look identical to this:
```
BUS=="**[COLOR="Red"]usb[/COLOR]**",SYSFS{product}=="**[COLOR="Red"]iPod[/COLOR]**",KERNEL=="sd?2",NAME="ipod",SYMLINK="usbdevices/ipod"
```

Where **[COLOR="Red"]usb[/COLOR]** and **[COLOR="Red"]iPod[/COLOR]** are the BUS and product information you extracted just above.  KERNEL="sd?2" will look for the sdX2 (where "X" is the alphanumeric of the node and 2 is the 2nd partition of your ipod's hard drive.)  NAME="ipod" and SYMLINK="usbdevices/ipod" will create the persistent node at /dev/usbdevices and a symlink at /dev/usbdevices/ipod.  Now, we need to actually create those folders, and we'll make the mount point while we're at it:
```
sudo mkdir /dev/usbdevices
sudo mkdir /dev/usbdevices/ipod
sudo mkdir /media/ipod
```

Next, we need to edit fstab so that your computer knows how and where to mount your ipod.  We'll back up the original, and then edit:
```
sudo cp /etc/fstab /etc/fstab_backup
sudo kate /etc/fstab
``` 
Add this line at the bottom:
```
/dev/usbdevices/ipod  /media/ipod vfat defaults,umask=000,auto,rw,user 0 0
```
Save this file (Ctrl + S) and close (Ctrl + Q).

Now, we just need to restart udev:
```
sudo /etc/init.d/udev restart
```
Then, quickly check that the new node as been created:
```
user@kubuntu:~$ls -l /dev/ipod*
brw-r-----  1 root plugdev 8, 49 2006-12-17 20:53 /dev/ipod
user@kubuntu:~$ls -l /dev/usbdevices/
lrwxrwxrwx  1 root root 17 2006-12-17 20:53 ipod -> ../ipod
```

Finally, do a:
```
sudo mount -a
``` to mount everything in your fstab.

At this point, your ipod should be mounted to /media/ipod.  You can check this by:
```
cd /media/ipod
ls
```
If you get an output that looks like:
```
Calendars  Contacts  iPod_Control  Notes  Photos
```
Then you're mounted!

If you don't see it the first time, it may be helpful to restart X...  Now, you just need to tell Amarok that your mount point is:  /media/ipod and you should be able to connect!

Like I said earlier, I did all this through remote administration, so troubleshooting particular errors may be difficult on my end.  Please let me know if I said anything stupid and I'll correct it right away.

---

### Post by madcow72 on 2007-02-12
Hey, just curious if this has helped anyone, or if it was a totally useless howto?  Looking through the forums, I don't think that I was the only person having trouble with a 2nd Gen ipod in Edgy...

---

### Post by Jockster on 2007-03-03
Wow! Thanks for this. My ipod has never mounted automatically, and just recently I have been unable to mount it at all, even using the command line. This fix has sorted all this - an icon now automatically appears on the desktop when I plug it in. I've no idea what the fix does, but it works. Thanks again!

Forgot to say - I used the first fix above!

---

### Post by madcow72 on 2007-03-04
Great!  Glad to hear that all that writing helped somebody out!  Thanks for letting me know.

---

### Post by el_rata on 2007-04-14
this stuff helped me too man ... !!! thnx !!!!

---

### Post by tarahmarie on 2008-09-11
Hey, I used the complicated long fix word-for word.  It worked!  Thank you very much!

One addition; I got an error message when trying to mount -a after creating the fstab line about the ipod not being a block device.  Rebooting fixed the problem; when I rebooted, the ipod was automatically mounted.

Also, when I opened amarok, I had to delete the old device that amarok had found, quit and restart amarok, and create a new device by manually adding a device with the apple ipod plugin and defining the mount point at /media/ipod.

Hope that helps.

---

### Post by barsofham on 2008-09-25
Quick warning if you're running Hardy. Do not use the first fix. I used it and I was not able to log into gnome. I think the problem is that the packages are out of date. I had to run sudo apt-get install -f to fix the problem.

---

