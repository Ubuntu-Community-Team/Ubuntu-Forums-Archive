---
title: "[SOLVED] Cannot empty trash in usb memory device"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-10
I have a USB memory "stick" of 256 meg. 

Using the file manager, I have done a Ctrl-H to see the .files. I have tried to empty the trash (.trash and stuff) so that I can copy a directory of 150 meg into the stick. I get an error message that the stick is too full, try to delete message or something. File properties of the device shows 192 meg used. That's not true. Maybe as much as 10 meg of non-trashed files is on or in the device. See attached screenshot.

---

### Post by drascus on 2008-05-10
Just so I understand you get that message when you try to empty the trash? for whatever you may have to do this from command line. I would run the mkfs command on the usbdisk in order to completely wipe it.

---

### Post by Mark_in_Hollywood on 2008-05-10
No, I get the message when I try to copy a directory into the USB memory stick.

I'm happy to mkfs, but need the entire command structure. And can't GParted do this as well?

---

### Post by Gazneth on 2008-05-10
```
gksudo nautilus 
``` will get you root privileges and then you can delete the .trash file. My new Hardy install prompts to empty trash when I unmount the drive, very nice.

---

### Post by Mark_in_Hollywood on 2008-05-10
I have solved the problem. I have ctrl-A to select all the files on the memory stick. Then a ctrl-T to move all to the trash. That brought up a request about "can't move to trash, do you want to delete"

I chose delete.

The stick emptied and I've copied my files over.

Thanks,Linux Community!

---

