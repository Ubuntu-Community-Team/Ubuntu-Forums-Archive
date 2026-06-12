---
title: "how do write usb"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by PNY on 2012-04-09
Im finding that I cant write to any usb device such as flash drive phone even SD card will not recieve files. I am told that I do not have permissions too write to the device. is there a simple way to change these permissions preferably without the use of the terminal. I can use the terminal but I feel there must be an easier way... you know ...its not a complicated thing I am trying to do, just copy a file. 

OK thanks for reading. your thoughts and ideas are appreciated.

---

### Post by Basher101 on 2012-04-09
you must edit your fstab i think, for permanent changes. The fstab file is where your device IDs are saved and what to do with them (e.g. permissions, mounting, etc.)

a more easier way is to just launch nautilus with admin privileges. To do this press alt+F2 and type ```
gksu nautilus
``` enter your password and you can copy your files.

---

### Post by PNY on 2012-04-09
i get ...destination is read only error.
Im trying to write a few mp3s to a micro usb in a phone.

---

### Post by Basher101 on 2012-04-09
how do you connect the micro with your computer? do you plug it in with an adapter or connect the phone with a USB cable?

---

### Post by PNY on 2012-04-09
useing a cable... ur gona tell me i need to take the card out of the phone arnt you?:lolflag:

---

### Post by PNY on 2012-04-09
thing is, i had an sd card in the machine that i could write to using the gksu method, but it was writing at 13kb per second and was going to take 2.5 hrs to copy the file so i think this method is unsatisfactory. 

I did do a search for fstab inside gksu nautilus and it came up with a bunch of files folders and programs...  I guess one of these is the files that needs to be revised. 

The thing that gets me is that i didnt change the permission on these disks and i think i have had write access to them in the past... i guess that makes it a bug if ubuntu is changing the write permissions without permission from the user... abit to secure for its own good we could say.

any thoughts?

---

### Post by Basher101 on 2012-04-09
had that too, just unplug and replug (sometime it got normal again..not sure what causes this)

anyways, Windows is better at copying stuff to devices. It is something with the kernel, when i copy a lets say 1 GB file to a usb stick or anything else thats not the hard drive, it is first fast (20 MB/s) but slows down rapidly until 1 MB/s or so. Once its finished copying, it says that it is writing data from the cache to the USB (this takes another 20 minutes or so).

---

