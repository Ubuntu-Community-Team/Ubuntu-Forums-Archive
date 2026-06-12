---
title: "Invalid version?"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by memyselfnie on 2011-12-29
Lotta weird things going on right now, not the least of which:  Tried to download both 11.04 + 11.10 to a 10 gig stick.  Both times got an error:
An uncaught exception was raised: invalid version string: GNU/Linux
Anybody???

---

### Post by memyselfnie on 2011-12-29
I should say "Install" rather than download.

---

### Post by Paqman on 2011-12-30
You'll want to put just one disk image at a time onto your stick. Follow the instructions [here]("http://www.ubuntu.com/download/ubuntu/download") about preparing a bootable USB stick.

---

### Post by mcduck on 2011-12-30
> **memyselfnie said:**
> Lotta weird things going on right now, not the least of which:  Tried to download both 11.04 + 11.10 to a 10 gig stick.  Both times got an error:
An uncaught exception was raised: invalid version string: GNU/Linux
Anybody???

How exactly are you trying to put the two Linux images on the USB drive? What tools are you using, and what exactly are you doing? And have you validated your disc images after download (using the MD5 checksums available at Ubuntu's download site)?

If you are using something like the Startup Disc Creator or Unetbootin, you'll only be able to add one image per USB drive. If you are making actual installs, you should be able to install multiple systems, each on their own partitions, just like if you were installing to a hard drive.

If you actually want a USB drive that can be used to install many different Ubuntu versions you'll need to do that by installing Grub2 on the USB drive and then adding the .iso images on the drive and configuring the grub.cfg by hand to look for those images.

---

### Post by memyselfnie on 2011-12-30
Was trying to just put one image on the drive.  Got the error with 11.04,
then again with 11.10, using the startup disk creater in 11.04.  Didn't do anything to the disk (that I know of). All because the cd player in the machine I was installing to mysteriously quit (no power).

---

### Post by memyselfnie on 2011-12-30
Re-downloaded 11.10, re-tried disk creator, with a new error code: org.freedesktop.DBus.Python.dbus.exceptions.DBusException: com.ubuntu.USBCreator.Error.NotAuthorized
DECIDED 11.10 NOT NECESSARY, CRAP!
STUCK WITH MINT 10

---

