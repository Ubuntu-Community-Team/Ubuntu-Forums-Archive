---
title: "Save folder to pen drive?"
date: 2015-09-03
forum: New to Ubuntu
---

### Post by theon2 on 2015-09-03
I have created a folder with a lot of my football info. Could someone tell me how i might save the folder onto my pen drive please.

---

### Post by tristan16 on 2015-09-03
Plug in your pen drive and open it by clicking its icon in the launcher. Open the folder you would like to copy, and drag-and-drop it onto the pen drive. If it's a large folder, you'll see a copying progress window.

---

### Post by theon2 on 2015-09-03
Hi Tristan16
I have already your suggestion and all i get is:

The folder "Football" cannot be copied because you do not have permissions to create it in the destination.
I have also tried to log in as "root" but with no success.

I did open a terminal and typed: sudo cp Football /media/Theon/2ba36e70-4f1d-4309-b366-72a2d713dfee
but all i got was - omitting Football?

I'm lost

---

### Post by monkeybrain20122 on 2015-09-03
What is the file format of your pendrive?  If it is in ext4 then it probably enforces credential checking (so either chown the pendrive or reformat it to FAT) Also to copy folder with command you need the -r flag, "cp -r path/to/folder"

---

### Post by theon2 on 2015-09-03
After all the fuss and bother i did as monkeybrain20122 suggested and reformatted the USB drive to FAT32 and then i simply dragged and dropped the folder. Big thanks for all the help.

---

### Post by Geoffrey_Arndt on 2015-09-04
There is also another way to copy the files to a Linux based usb-flash stick . . . gksu nautilus, and then, open the stick via nautilus, goto properties tab, adjusting the owner to you.   (might have to install gksu first).   Using a linux file system is a bit more secure too.

---

