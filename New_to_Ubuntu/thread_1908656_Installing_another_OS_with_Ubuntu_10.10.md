---
title: "Installing another OS with Ubuntu 10.10"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by IsThisThingOnOrWhat on 2012-01-13
Got a new lenovo desktop, and an extra internal 2TB hard drive. I immediately installed Ubuntu 10.10 on the 2TB and soon after I wiped the stock internal 1TB with Windows 7 on it. Now I want to install Windows XP on the internal 1TB but I'm having issues. When I go to the boot from other drive screen in the pre-GUI stage of the OS start up, I select the CD drive (or USB, I've tried both with Ubuntu 10.04) and the screen goes black and then takes me to the boot menu, which has a couple of versions of 10.10 and the old Windows 7 that was erased... There doesn't seem to be any options to begin installing the new OS. I'm sure I'm missing something really easy on this one. Thoughts?

---

### Post by C.S.Cameron on 2012-01-13
Did you do a Live install to the USB or a Full install?
Only the Live install, (usb-creator, Unetbootin), has an option to install Ubuntu.

EDIT:
Oops I see it is XP you wish to install, you need the install CD for this.
I think there are also methods to make an install USB.
It might also be possible to use VBox to make a virtual XP machine and then clone this to the internal drive.

---

### Post by oldfred on 2012-01-14
You normally do not boot a CD or LiveUSB from grub, but use BIOS to choose boot device. If you want to boot from liveUSB you could manually add a chainboot entry and I think that would work if your system allows you to boot from USB, but easier to just use BIOS.

---

