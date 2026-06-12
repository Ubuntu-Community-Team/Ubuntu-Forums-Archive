---
title: "[SOLVED] Can only access usb digital camera as root"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by anewguy on 2008-05-07
I have a couple of digital cameras that I hook up to my PC with a USB cable in order to download video and still pictures from them.  Currently in Hardy, I have to su to root to access the cameras when they are plugged in.  In Feisty and Gutsy I had added 2 lines to the 40-permissions.rules file that took care of this (they set permissions on the USB device depending on its ID).  There is no place for those lines in the 40-permissions.rules file in Hardy.  There is a place for them in the 40-basic-permissions.rules file which supposedly gets processed before the 40-permissions.rules file.  I have added the lines there with no effect.

Can anyone help with this?  The lines in question are in red from this extract from 40-basic-permissions.rules:



# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",		MODE="0664"
[COLOR="Red"]SUBSYSTEM=="usb_device",SYSFS{idVendor}=="0dca",
SYSFS{idProduct}=="0027", MODE="0666"
SUBSYSTEM=="usb_device",SYSFS{idVendor}=="167b",
SYSFS{idProduct}=="0101", MODE="0666"[/COLOR]

---

### Post by Daveth on 2008-05-07
Is this true of all of your usb devices? I ask as I just plug my panasonic camera in via its usb cable, and have full access without needing rule revisions. Have you sought to mount the device with a persistent name then?

---

### Post by spiderbatdad on 2008-05-07
wondering if the user account has sufficient permissions under System>>Administration>>Users and Groups>> (account) >>Properties>>User Privileges.

---

### Post by t0p on 2008-05-07
I also find your problem puzzling, as I have no difficulty accessing via usb my Fujifilm digital camera.  Under **Users & Groups**, have you perhaps disabled your user's privilege to "access external storage devices automatically"?  I'm pretty sure that a usb-connected camera would be classed an "external storage device".

---

### Post by PinkFloyd102489 on 2008-05-07
I forget how to do it, but add yourself to the "plugdev" group. There's a way that you can edit a file to do so.

Let me check around and I'll edit my post with the location.

---

### Post by anewguy on 2008-05-07
Well, this will probably throw some mud in the water, but......

The 2 cameras in question are actually CVS Pharmacy One-time Use Digital Camcorder and a CVS Pharmacy One-time Use Digital Camera modified as per Camerahacking.com so as to be reusable. As such, these devices need a special set of software to be accessed.  They are not standard digital cameras and as such do not show up as storage devices.  Normally they just show in a lsusb, but for some reason I'm not getting that right now or I would post the details.

The 2 lines had to be added for permissions in both Feisty and Gutsy to override the default ownership of root.  When root, it creates all of the downloaded files as owned by root even though they are in a user folder.  This creates some needless headaches.  The 2 lines do not include a group so there is no group to assign a user to to get access.  They instead say for devices of that particular usb id give the device world access permissions.

Again, these are anything but "standard" devices unfortunately, so the above are needed.  I just don't understand why they don't "take" when they are in 40-basic-permissions.rules.

Any help would be greatly appreciated, and thanks for the responses so far!!  :):)

EDIT:  Forgot to mention, already a member of the plugdev group - it makes no difference.

---

### Post by anewguy on 2008-05-08
Anyone?

---

### Post by warbread on 2008-05-08
Interesting.  Can you post what instructions specifically you used, as well as what special softwawre it is you're using?

I have no idea if I can help, but I'm interested in finding out.

---

### Post by anewguy on 2008-05-08
> **warbread said:**
> Interesting.  Can you post what instructions specifically you used, as well as what special softwawre it is you're using?

I have no idea if I can help, but I'm interested in finding out.

The above mentioned lines are what allowed world access.  The coding itself is a merge of avidownload and pv2tool from sourceforge that I merged together myself and am now adding a GUI to.  That code uses low-level reads and writes on usb endpoints via calls to functions in the libusb development libraries.

As mentioned, this all worked fine in Feisty and Gutsy, and the program itself still runs fine in Hardy - you just have to run as root to get access to the usb devices.  This in turn creates folders and files in the users' directory, so suddenly they have files and folders they can't delete, etc., because they don't own them.  The above mentioned changes to the rules permissions files previously granted world access to just those 2 devices, and this is the part not working in Hardy.

Thanks!  :):)

---

### Post by warbread on 2008-05-08
But what instructions did you use for the camera itself?  Or, what model is the camera that you're using?  From what I understand on that forum, there's a few different CVS models of cameras.

---

### Post by anewguy on 2008-05-08
> **warbread said:**
> But what instructions did you use for the camera itself?  Or, what model is the camera that you're using?  From what I understand on that forum, there's a few different CVS models of cameras.

Ah....well, I've had the program working with 3 different camcorders (2  model 230's, and a model 210 [I think -I've loaned it out to my sister and expect it back soon) as well as camera model 410.  I would give you the specs for the firmware, etc., but really that isn't the problem - I can talk to them just fine with the program if I run as root.  The problem is the USB device permissions.  Again, this was solved in Feisty and Gutsy with the above 2 lines, and there is a similar set of lines that go in for a standard debian installation (if you search the camerahacking.com site for the camcorder and a reply by Saturnnights from last fall, you'll find the thread where I mentioned what I did and how SaturnNights applied it to standard Debian).

Thanks again! :):)

---

### Post by anewguy on 2008-05-09
Problem solved - a syntax changed in the move to Hardy.  Here's a link to the thread where it covers more detail:

[http://ubuntuforums.org/showthread.php?p=4916040#post4916040]("http://ubuntuforums.org/showthread.php?p=4916040#post4916040")

---

