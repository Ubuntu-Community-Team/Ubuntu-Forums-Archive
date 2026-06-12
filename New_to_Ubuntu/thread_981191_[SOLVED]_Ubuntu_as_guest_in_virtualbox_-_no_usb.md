---
title: "[SOLVED] Ubuntu as guest in virtualbox - no usb"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by anewguy on 2008-11-13
I've checked the forums for VirtualBox related USB issues, and so far have not found one in reference to my problem:

I have Windows XP Pro SP3 as the host, running Ubuntu 8.04 as a guest VM in VirtualBox.  I set up a blank filter (supposedly allows all USB devices) and have tried filters for each device, but none of my USB devices show in Ubuntu.

A "lsusb"  simply returns the 2 busses - no devices:

dave@dave-desktop:~$ sudo lsusb
[sudo] password for dave: 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
dave@dave-desktop:~$ 



Plugged in at start, plugged in after start, etc., seems to make no difference.  

Zero devices show.

I assume I'm doing something idiotically wrong, but I checked the VirtualBox documentation and the forums, and just can't find my problem listed.  I tried some of the things listed - like adding a line to fstab.  I didn't mess with permissions yet, since if I'm not seeing the devices I can't imagine the permissions being the problem - but I could be very wrong.

Any help would be greatly appreciated!

Thanks in advance!
Dave :)

---

### Post by Thingymebob on 2008-11-13
Which virtual box are you using? the Open source edition doesn't allow passing through USB devices. You need the closed source edition.

---

### Post by anewguy on 2008-11-13
Well, I THOUGHT I downloaded the closed source one, but I wonder how I can tell?  It does give me USB options on the console, and if I turn on turn off the 2 controller options, the 2 controllers disapear from a lsusb.  If it helps any to know what version I did download, it's name is:

VirtualBox-2.0.4-38406-Win_x86.msi

Thanks!
Dave :)

---

### Post by snova on 2008-11-13
I believe you have to add some kind of "filter" that defines which devices are visible to the guest OS. Plug it in and create one for the device, that may work.

If you downloaded it from their website, it's probably the closed source edition. Either way, if the guest OS can see a USB bus at all, it probably is.

---

### Post by bodhi.zazen on 2008-11-13
I seem to recall that as you installed VirtualBox on Windows the installer ask if you want to enable USB devices ? Not sure on that one.

I found this link today :

[http://opensourceexperiments.wordpress.com/2008/04/25/virtualbox-how-to-gotchas-involved-in-making-a-usb-external-hard-disk-device-work-on-windows-host/](http://opensourceexperiments.wordpress.com/2008/04/25/virtualbox-how-to-gotchas-involved-in-making-a-usb-external-hard-disk-device-work-on-windows-host/)

---

### Post by anewguy on 2008-11-13
Thanks!  I took a look at that site but unfortunately I never get that far.  I went so far as to uninstall/reinstall VirtualBox being sure I had all of the pieces marked for installation, including USB support.

I then went to set up the VM and in USB I enabled both controllers.  I then clicked on the "add" so I could see what devices it could see at that point - all it saw were my USB keyboard and USB mouse - nothing there for the other connected devices.  So, I shut down VirtualBox, unplugged/plugged in my USB flash drives and 1 of my cameras, then restarted VirtualBox.  This time I could see me devices in the USB section when I did an add, so I added 3 of them.

At this point I am waiting for Ubuntu to reinstall in the VM, then I have to do some updates and install a few packages.  After that I'll know if Ubuntu is able to see the devices.  I will post back then with the results.

Thanks again!
dave :)

EDIT:  Finished the Ubuntu install.  Never unplugged the USB devices, they were found when setting up the parameters for the VM, but when the Ubuntu guest is running and I do "sudo lsusb", no devices show, only the 2 busses.  My 2 flash drives that I have plugged in weren't seen or mounted.  I have to believe I am doing something stupidly wrong, but I'll be darned if I can get it to work!

---

### Post by medley on 2008-11-13
> **anewguy said:**
> I've checked the forums for VirtualBox related USB issues, and so far have not found one in reference to my problem:

I have Windows XP Pro SP3 as the host, running Ubuntu 8.04 as a guest VM in VirtualBox.  I set up a blank filter (supposedly allows all USB devices) and have tried filters for each device, but none of my USB devices show in Ubuntu.

A "lsusb"  simply returns the 2 busses - no devices:

dave@dave-desktop:~$ sudo lsusb
[sudo] password for dave: 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
dave@dave-desktop:~$ 



Plugged in at start, plugged in after start, etc., seems to make no difference.  

Zero devices show.

I assume I'm doing something idiotically wrong, but I checked the VirtualBox documentation and the forums, and just can't find my problem listed.  I tried some of the things listed - like adding a line to fstab.  I didn't mess with permissions yet, since if I'm not seeing the devices I can't imagine the permissions being the problem - but I could be very wrong.

Any help would be greatly appreciated!

Thanks in advance!
Dave :)

Make sure you have the guest additions installed. I'm using VB 2.0.4 right now, Kubuntu under Vista, and my USB is working. Don't have first hand experience with XP as the host, but I don't see why it shouldn't work. Just make sure you have the guest applications installed.

---

### Post by anewguy on 2008-11-13
Guest additions are installed, the suggested line is in /etc/fstab, and I even added a line to one of the files in /etc/init.d as recommended in another post.  Net result - no usb devices being seen.

I do development in GTK and C in both Windows and Ubuntu (code sharing between OS's) using libusb, and was really hoping I could get this to work. 

I can't dual-boot on the PC with Windows on it, as it is a work computer (even though I work from home it has to remain purely Windows for the work).

I don't really know what to do right now.  I think I am out of options and am going to have to give up on Ubuntu in a VM for now.  Sure wish it would work.

Thanks for the help!
Dave :)

---

### Post by Vadi on 2008-11-14
Tried starting the VM without usb devices plugged in or with them plugged in?

(edit, [http://forums.virtualbox.org/](http://forums.virtualbox.org/) is probably the place you'd like to ask this too)

---

### Post by anewguy on 2008-11-14
Yes - I tried both ways - once with them plugged in, the other with them not when booting the VM.  Even though the last time around it didn't see any of the devices (in Ubuntu), it still locked them out of Windows when I closed the VM and even a restart wouldn't solve it - I had to actually power off the PC.

Another thing I find interesting, and I don't know if this has anything to do with it, is that when I plug in a USB device, such as a flash drive, Windows (XP Pro SP3) never shows the little usb icon in the system tray, and therefore I can't do a "safely remove hardware" on the USB devices.  Perhaps what ever is causing that in Windows (the devices are accessable, just no icon in the system tray) might be what is preventing Ubuntu from seeing the devices.

Perhaps there is some configuration option or something in Windows itself which I have missed.

Thanks again!!
Dave :)

---

### Post by gbold on 2008-11-14
I am running Intrepid as a VM on top of XP (Dell Precision M4300) and I just tried using a Maxtor external drive.  Here's what I did (and it worked):

I went into the Ubuntu settings and enabled the USB Controller and USB 2.0 Controller, then added the USB filter with empty strings.  I safely removed the Maxtor external drive and started up Ubuntu.  After the OS had loaded, I plugged in the Maxtor drive and I got a New Hardware found message for WinXP so I let it install the drivers for the VBox USB that it found.  I then shutdown Ubuntu, unplugged the drive from XP (it wasn't seen in the Safely Remove Hardware in the system tray) and restarted Ubuntu.  Once the desktop was loaded I re-plugged in the Maxtor drive and voila, the drive showed up on my Ubuntu desktop.
Hope this helps-
Greg

Edit-
I found out just now that you'll get a new USB device found for the host (XP)system for each different USB drive you plug in.  Just tried my USB flash drive and it worked after the drivers got loaded in XP, unplug/replug the drive.

---

### Post by anewguy on 2008-11-15
Thanks for the reply!  I just tried this - emptied out all the filters and went back to just an empty one again.  Started Ubuntu, waited for everything to load.  Plugged in Lexar Firefly USB flashdrive - Windows did it's ding-ding thing, asked what I wanted to do with the drive - I said nothing and closed out of that.  Never did show in Ubuntu - never was mounted - nothing.  "lsusb" still shows only the 2 busses, no devices.  the only USB devices the VM seems to know about are my keyboard and mouse.  Everything else goes through a different port - using the same one from the rear I tried direct-connect and a hub, neither made any difference.  Tried front USB port - still no difference.  I just don't get it - they SHOULD be there!  Maybe I'll get rid of VirtualBox and the download for it, and start again back at Sun and double-check I download the correct version.  Something so simple, so I must be doing something wrong!

Thanks again!
Dave :)

---

### Post by anewguy on 2008-11-15
Okay, I started completely from scratch again.  I completely removed any VM's, uninstall VirtualBox.  I went to Sun's site and downloaded VirtualBox again - there was another option there for the open-source version so I know the one I downloaded was not the open-source version.  I installed VirtualBox and started it up.  Created new VM with new virtual disk (the auto-sizing kind, if this makes any difference at all).  Then went to USB, enabled both controllers and created a single filter that is all blank (according to the docs, this is supposed to allow ANY USB device).  Started VM, installed 8.04, rebooted VM, went through Synaptic and installed build-essential, the libusb development libs and the GTK 2 development libs.  Rebooted the VM again.  Plugged in a Lexar Firefly USB flashdrive - doesn't show.  Plugged in an Omnitech USB flash drive - doesn't show.  Again, "lsusb" is just showing the controllers.  If I do the VM "devices" on the VM menu bar and go to USB, only my keyboard and mouse show there (interesting they don't even show in the "lsusb").

So, now I'm wondering, did all of you download VirtualBox via Sun's site, or did you go through the VirtualBox.org?  They both show as the same file name and the same size.

I just can't figure this out - others get this working - so I have GOT to be doing something wrong or missing something, but I have no idea what that could be.

Thanks again,
Dave :(

---

### Post by anewguy on 2008-11-15
I also followed the advice in this link:

[http://https://help.ubuntu.com/community/VirtualBox#USB]("http://https://help.ubuntu.com/community/VirtualBox#USB")

Then added a group called vboxusers and added my user id and root to that group.

Still no usb devices showing.:(

---

### Post by anewguy on 2008-11-16
Also followed this link, doing everything in it, and adding the 2 packages as others suggested.  Still no USB devices showing.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html")


If, before starting the actual VM, using the VirtualBox control panel I can add the USB devices.  When I start the VM, they don't show.  However if I move the cursor to the bottom of the VM pane and over the USB cable symbol, I can select a device and then I get this in a VirtualBox error box:

Failed to attach the USB device LEXAR JD FILFLY [1100] to the virtual machine ubuntu 8.04

USB device "LEXAR JD FIRFLY" with UUID {0425d990-c913-477d-b7f2-1c6aa339d188} is busy with a previous request.  Please try again later.

Result Code:  E_INVALIDARG (0x80070057)
Component:  HostUSBDevice
Interface:  IHostUSBDevice {173b4b44-d268-4334-a00d-b6521c9a740a}
Callee:     IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}


So, is the device busy on a host request (I already did the "cancel" when Windows recognised the device), or is busy on a guest (Ubuntu 8.04) request?

---

### Post by biotechie on 2008-11-16
Normally we install an OS once and maybe update once for each new version. In setting up the virtualized stuff, we may do multiple attempts at doing installations.  

Is there any chance that you did what I once wasted a week on: not loading specialized drivers that came with my motherboard on a CD, and with some peripherals? That had to be done after every completely new installation of the standard Windows CD, for example.  Not loading those drivers caused a lot of peripheral devices not to work, and mystified me.

---

### Post by anewguy on 2008-11-16
I appreciate the reply, but no, the motherboard and all other drivers were loaded in Windows (the host OS).

Thanks again!
Dave :)

---

### Post by anewguy on 2008-11-17
Just FYI - I'm following another post for the exact same problem in the virtual box forums:

[http://forums.virtualbox.org/viewtopic.php?p=46449#46449]("http://forums.virtualbox.org/viewtopic.php?p=46449#46449")

Any information that helps from either forum will be posted to the other.  At least I know I'm not alone.

Dave

---

### Post by anewguy on 2008-11-18
Another FYI, if it helps in debugging this at all (so far the virtualbox users forum hasn't had any answers, none found on the web anywhere):

prior to starting the VM, the device shows as captures in vboxmanage.  I start the VM - no device, doesn't even show with a right-click of the USB devices in the bottom status bar.  Yet vboxmanage still shows the device as captured.  I have to shutdown the VM, remove the device, remove the device-specific filter, plug the device in and do the add of a filter, selecting the device.  Then start up the VM again.  It shows on a right-click of the USB icon on the bottom status bar, but if I click on that I get the busy error box.  This entire time vboxmanage still shows the device as captured.

I'm wondering if this is some bug with XP SP3 and virtualbox, as the other posts I have read have indicated either XP SP2 or Vista.

Any help would be greatly appreciated!!  The busy error box should be saying something to someone - unfortunately Sun doesn't have any live support for virtualbox that I have found, nor do they have an email address for support.

Dave :(

---

### Post by anewguy on 2008-11-19
I have some big progress to report, but still looking for help.

I run libusb and GTK in both Windows and Linux because I do cross-platform development.  I got to thinking about it and thought maybe the libusb stuff in Windows (the host OS) was messing this up, so I removed libusb from Windows for now.

I next started VB and removed all USB filters, then just added an empty filter.  I closed and restarted VB, then started the VM for the Ubuntu guest OS.  I then plugged in the USB device and nothing happened - even vboxmanage list usbhost showed the device only as busy now.  So, I went to the USb icon on the bottom status bar of the VM, right-clicked and my device was there so I clicked on it - right away Windows came up saying it had found new hardware, a virtualbox USB device, and installed the driver for it.  It had NEVER done that before!  To top it off, I never got the busy error box, and at this point vboxmanage list usbhost now showed the device as captured - so I think half of the puzzle is solved.  However, in the guest (Ubuntu) OS I still don't see the devices.  I modified the mountdevfs (?) script and also the 40-basic-permission-file as recommended elsewhere.  I created a group called virtualbox in Ubuntu and added myself to it (to match the changes in the aforementioned 2 files). Logged out and back in - no difference.  Restarted the guest (Ubuntu) OS, still not seen.

However, I do believe the devices are finally getting "switched" to virtualbox now that I deleted libusb.  There must be something in the guest Ubuntu OS for permissions or something that it not allowing me to see them yet.

So, progress!  But....help still needed!  Any ideas?

Thanks in advance!
Dave :)

EDIT:  I did get the VM to finally see my first flash drive!!  Now I'm working on the second and my other devices.  It seems for each new USB device, Windows detects new hardware and installs the virtualbox USB driver, then I have to shutdown the VM and close VB, then restart it and it will see the devices!!

So, I guess I can marked this as "solved", but I'll probably open another about libusb and virtualbox, just not sure where to open it!

Thanks SO MUCH to everyone!

Dave :) :)

---

