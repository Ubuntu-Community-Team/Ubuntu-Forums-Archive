---
title: "[SOLVED] Hardy - USB Device Permissions"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by anewguy on 2008-05-06
I had put the following 2 lines in my 40-permissions.rules file in 7.04 and 7.10 to allow non-root access to the 2 devices.  I let the upgrade to Hardy replace the file so I would have the newest.  Now there doesn't appear to be a place for them in 40-permission.rules, but I did see the 40-basic-permissions.rules is in the format of the old file so I added the devices there in the USB fs section.  Still no go - I have to be root to access the devices.  Can someone explain what has changed and where these statements need to go now?

Thanks!:)

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0dca", SYSFS{idProduct}=="0027",
MODE="0666"
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="167b", SYSFS{idProduct}=="0101", MODE="0666"

---

### Post by anewguy on 2008-05-06
Any ideas?

Thanks! :)

---

### Post by anewguy on 2008-05-07
Can anyone help me on this or at least direct me to some documentation that might explain this.  It appears that the 40-permissions.rules file changed and I no longer know where these assignments should go.  :)

---

### Post by anewguy on 2008-05-07
Please excuse the bump, but perhaps someone has come online now that may know that answer.

---

### Post by anewguy on 2008-05-08
I have the following post open for which I have not gotten a solution.  This is something that worked in Feisty and Gutsy but for some reason doesn't seem to work in Hardy.  It deals with the permission files in the /etc/udev/rules.d  directory.

There must be a solution to what I need to do in Hardy, unfortunately no one seems to know.  

Help? 

[http://ubuntuforums.org/showthread.php?p=4897880#post4897880]("http://ubuntuforums.org/showthread.php?p=4897880#post4897880")


EDIT:  BTW for standard Debian, I was told the lines mentioned go in the 20-permissions.rules file, but there is no such file in Ubuntu.

---

### Post by spiderbatdad on 2008-05-08
Looked at your thread. MODE=0666. Those are your permissions.
There are no execute permissions there. That might be part of the problem.

Permissions, in order are U=user G=group O=other.

Read=4  Write=2  Execute=1

0666= user/rw  group/rw other/rw

Also consider launchpad as a resource for troubleshooting: [https://launchpad.net/](https://launchpad.net/)

---

### Post by bodhi.zazen on 2008-05-08
Threads merged. I know it is frustrating sometimes, but please be patient.

We have an unanswered team and if you bump your own threads there is no way for them to find your problem as unanswered.

Also please do not start multiple threads on the same topic, it only makes more work and causes confusion.

---

### Post by anewguy on 2008-05-09
Sorry everyone - I didn't mean to make anyone upset, so I am sorry.  I just couldn't figure out why this worked in Feisty and Gutsy but not in Hardy.  I guess I also don't get why the permissions worked in those 2 but not in Hardy, except to say I don't need to execute the USB device - I need to read it via calls in libusb.  So I wouldn't think I'd need execute permissions on a device.

The program in question is now a GUI'd application using GTK (I just finished that), where as the old was a command line application.  But I know that makes no difference - especially considering the old command line application will not access the USB device now either unless it is run via sudo.

Bohdi.Zazen - what's the status now?  Do I wait to see if someone has any ideas, and if so, how, or is there a legit problem in the way the permissions are being handled in Hardy (perhaps a change to libusb in some way?).

Again, sorry.

---

### Post by bodhi.zazen on 2008-05-09
I am not understanding your problem. USB devices auto mount for me here ...

What device are you trying to configure or what is it about permissions that you feel needs changing ?

---

### Post by anewguy on 2008-05-09
I have a few "special" USB cameras - CVS one-time use camcorders and a CVS one-time use digital still camera hacked for reuse as per camerahacking.com.  The 2 lines mentioned earlier for 40-permissions.rules were needed in Feisty and Gutsy so that someone other than root could access them.  These cameras don't use standard drivers or communications protocols for digital cameras - hence the use low-level usb calls to libusb to do it.  For the still camera, it has to be in bulk-write and bulk-read mode on USB endpoints for the device.  There is also a "key" exchange at the beginning to unlock the camera or camcorder before any further conversation with the device can take place.

By default, when these devices get mounted, they are visible apparently by all users:

dave@dave-desktop:~/cvsdownload$ lsusb
Bus 004 Device 010: ID 167b:0101  <== the camcorder
Bus 004 Device 004: ID 03f0:7604 Hewlett-Packard Deskjet 3940


dave@dave-desktop:~/cvsdownload$ sudo lsusb
Bus 004 Device 010: ID 167b:0101  <== the camcorder
Bus 004 Device 004: ID 03f0:7604 Hewlett-Packard Deskjet 3940
Bus 004 Device 003: ID 050d:705c Belkin Components 
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:0053 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
dave@dave-desktop:~/cvsdownload$ 

Again, as a normal user:

dave@dave-desktop:~/cvsdownload$ lsusb -v

Bus 004 Device 010: ID 167b:0101  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x167b 
  idProduct          0x0101 
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               96mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Notice it permit the last operations - I assume because it's trying to actually "read" the device, and the device requires unlocking by the "key" first.


However, when the program tries to open and claim the USB device (again via libusb) it fails.  Change to "sudo" and it works fine.  The above mentioned lines were all that were needed before to let a "normal" user open and claim the device.  That no longer works in Hardy - it's as if it's ignoring the permissions some how.  Since I have added the lines to 40-basic-permissions.rules, which should do the same as before but makes no difference, perhaps something changed in the usb development library(ies).  With Hardy, I have libusb-0.1-4 and libusb-dev installed.

All I know is that with Feisty and Gutsy, via 40-permissions.rules, the USB devices where given 664 permissions.  When the 2 lines were added saying for this particular device from this particular vendor change the permissions to 666, everything worked.

In Hardy, those permissions appear to now need to be set in 40-basic-permissions.rules, and even at that have no effect - I must be a root user to open and claim the device.

Hope that helps explain it.

EDIT:  BTW, needless to say running as "sudo" seems (A) require the command line and (B) gives root ownership to the directory and files created by the application when it downloads videos or pictures.  This makes for a mess in the users' directory.

---

### Post by bumanie on 2008-05-09
I saw this post earlier and found it hard to follow. Usb devices automount in ubuntu unless they have been improperly unmounted. If you are getting some error message, please post it. I've never had to put any lines into a 'permissions.rules file' to get a usb device to work. I'm confused as to why you thought you had to do this, this may have been necessary for linux when usb's were new, but everything to enable usb function is now included in the kernel, and has been for some time.

---

### Post by anewguy on 2008-05-09
I'll try not to appear as frustrated as I am right now, so please bear with me.  These devices require a "key" exchange to unlock.  They also don't use "standard" USB communications as far as a camera device is concerned.  As such, when they are mounted, they follow the rules in (at least now in Hardy) is 40-basic-permissions.rules.  By default, the device is mounted with 664 permissions - it's owned by root and not world accessable:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",		MODE="0664"

 By adding the following to that file, it essentially says "for these 2 devices identified by vendor and product id, mount them as world accessable":

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0dca",SYSFS{idProduct}=="0027", MODE="0666"

SUBSYSTEM=="usb_device", SYSFS{idVendor}=="167b", SYSFS{idProduct}=="0101", MODE="0666"
 

I don't know how else to explain this.  They aren't "normal" USB cameras, they don't look like a flash drive, they don't look like anything.

When the device permissions default to root as they do, you have to run via "sudo" from a command line rather than from a GUI.  In addition, the program creates a folder and downloads the images into that folder.  Since running as a super-user, the folder and images become owned by root, not the user, even though they are in the user's home folder.  Try updating images and saving them back to that folder, or deleting them, and you need super user access again.  Not good.

As I said, the above lines solved the problem in Feisty and Gutsy - I know, I made the changes, it worked.  The same lines are added to a different file (I believe it is 20-permissions.rules) in standard Debian.

This is really all the clearer I think I can make it.  Remember, these are not "standard" USB devices, so they are recognized as cameras, flash drives, etc..


EDIT:  Here's the C code where the failure happens unless root user - trying to claim the device via a libusb call:

		if (m_p_handle)
		{
			wrk_x = usb_set_configuration (m_p_handle, DEFAULT_CONFIGURATION);
			if (wrk_x !=0)
			{ 
			    do_logmsg("Warning: Unable to set usb configuration (%d)\n",wrk_x);
                             return FALSE;
                        }


I know the code isn't as "fancy" as it could be, but the thing is it works.

the returned code is:  (-1076978200)



Soooooo......please somebody tell me either what stupid thing I am doing wrong or else what changed in either the device permissions handling (note it Hardy the USB devices where moved from 40-permissions.rules to 40-basic-permissions.rules) -OR- what changed in libusb such that now I have to be a root user no matter what.

This is why I marked my latest post on this, which was merged back here, as for a moderator or a guru.  I'm just an idiot, believe me, but I think there is much more to what is going on here than what the "normal" user with a "normal" device would run into.  Basically, the program is working as the driver for the device.

---

### Post by anewguy on 2008-05-09
Okay, for all of you who may have thought I was full of it, via a yahoo search of 40-permissions.rules and reading through a LOT of posts, I found this:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/210421]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/210421")

Basically, the syntax used in the 40-permissions.rules file prior to Hardy has changed.  In addition, other posts suggested that any user changes now need to be in a user-numbered-and-named.rules file higher than 40.

So, I removed the 2 lines from 40-basic-permissions.rules and placed them in a new file called 41-cvs-permissions.rules, modified them to fit the new Hardy syntax, and guess what - it works.

So, if someone else is having problems with device permissions, people should pay more attention to the udev files and the changes made to them for Hardy which caused the old syntax not to be recognized.  I suppose SOMEWHERE in some log file there are some cryptic error messages about this, but basically this is the fix.

Keep this in mind next time. :)

---

