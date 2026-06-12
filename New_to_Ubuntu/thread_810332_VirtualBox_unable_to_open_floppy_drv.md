---
title: "VirtualBox unable to open floppy drv"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-05-28
Bit of a noobi question..

I have a USB floppy for my lappy, but V/Box cant open it

[COLOR="DarkSlateBlue"]Cannot open host device '/dev/sdb' for read/write access. Check the permissions of that device ('/bin/ls -l /dev/sdb'): Most probably you need to be member of the device group. Make sure that you logout/login after changing the group settings of the current user.[/COLOR]

My USB RS232 comm port adapter works fine so I dont know if it is a specif USB issue or do I have to set permissions....which I cant work out...

Unfortunatly I have one old DOS programme that needs to see an a:\ drive to setup.....

And no Wine isnt an option...USB wont work there....after I spent much time getting stuff to work in it...:(

---

### Post by Ducatiboy Stu on 2008-05-28
Anyone......:confused:

Still cant work out how to give Vbox permissions to floppy

---

### Post by HotShotDJ on 2008-05-28
Ok.. these steps apply ONLY to the version of VirtualBox obtained through Sun... it does NOT work with the VirtualBox-OSE that you get in the standard repositories.

[LIST=1]
[*]Open System --> Administration --> Users and Groups
[*]Unlock the dialog (see "Unlock" button)
[*]Click On "Manage Groups"
[*]Click "Add Groups" and add a group called "usbusers" & write down the Group ID number.
[*]Check off the user(s) that you want to allow usb privilages in VirtualBox
[*]Click "OK" then "Close" then "Close" again.
[*]Open Applications --> Accessories --> Terminal
[*]type "gksudo gedit /etc/fstab" (without quotes)
[*]Add the following two lines to the end of the file:```
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=1001,devmode=664	0	0
```
[*]IMPORTANT:  Change "devgid=1001" to whatever number you wrote down in step number 4
[*]Save the file and close.
[*]Reboot your system.  You should now have full access to all USB devices in Virtualbox
[/LIST]

---

### Post by Ducatiboy Stu on 2008-05-28
MMMmmmm....I have the v/box OSE version

My other USB device works with it as a serial port device...

Shall give it a go

---

### Post by HotShotDJ on 2008-05-28
> **Ducatiboy Stu said:**
> MMMmmmm....I have the v/box OSE version

My other USB device works with it as a serial port device...

Shall give it a goUSB devices generally won't work at all in the OSE version.  If you need full USB support, you'll need to get [THIS]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") version.  Be sure to completely remove the OSE version (including the modules) before installing the Sun version.  Once installed, then go ahead and follow the steps I provided in my other post.  Those steps will have absolutely no effect for the OSE version.

---

### Post by niteshifter on 2008-05-28
Hi,

> My other USB device works with it as a serial port device...

That's because it's not appearing to the Guest as a USB device, but as a serial device through the Host.

As HotShotDJ just posted you need the PUEL version from Sun for full USB device access. He also left out a step - you have to either:

A) Select the USB device you wish the Guest OS to use from VBox's Devices Menu.

Or

B) Setup a USB Device Filter in the VBox GUI.

"A" acts like plugging / unplugging a physical device. For a device needed at Guest boot time "B" is the better option.

---

### Post by Ducatiboy Stu on 2008-05-28
Aaahh YES...that does make sense.....as Ubuntu sees the USB dev as a serial port, not a USB dev

Now I will have to re-install XP in V/Box and all the programs in it....:roll:

---

