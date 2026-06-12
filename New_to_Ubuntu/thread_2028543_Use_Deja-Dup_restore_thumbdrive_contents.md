---
title: "Use Deja-Dup restore thumbdrive contents?"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-07-18
I have a usb thumb drive (also called a jump or flash drive) installed in a usb port on this 'puter. The drive was formatted NTSF. It was part of my backup strategy. That is, Deja-Dup backed the contents of it as well as other drives.

One problem with the linux executables on the drive was that it couldn't be mounted in the way that usb removable drives are mounted in Linux. So, being a noob, when I couldn't find a way to eject the drive, I removed it, sadly while the 'puter was powered up. Now all the data is missing. Missing whether I'm using Ubuntu or Windows. The OSs don't see it at all.

Can Deja-Dup be used to restore the missing files?

---

### Post by tea for one on 2012-07-18
Good evening

Let's see if we can read/or identify the contents of the drive via the terminal:-

Close your OS and power off the PC

Insert the thumb drive into a USB port

Turn on the PC, log in to Ubuntu and open a terminal - Ctrl Alt t

```
gksudo nautilus
```

Enter password

This will open the file manager as a GUI

Click on File System (left pane of nautilus (file manager)

Click on media

Does your USB flash drive appear?

---

### Post by Mark_in_Hollywood on 2012-07-19
I don't use Gnome. Although I can. If that becomes necessary. Using Thunar, the object does not appear on the pane. It does appear in a terminal from the / direcory, using ls, LEXAR is in the list.

Opening this folder shows nothing inside it. This is from Thunar, not Nautilus.

---

### Post by tea for one on 2012-07-19
I was hoping that some files would appear..........

In your earlier post, you mentioned that you had backed up the contents of your thumb drive with Deja-Dup, have you tried to restore the back-up to a free partition to see exactly what appears?

One last little trick, using the terminal, navigate to your Lexar drive and try:-```
dir
``` instead of ```
ls
```

---

### Post by Mark_in_Hollywood on 2012-07-20
Both ls and dir return NO results. My original post asks: if the files on a thumbdrive are backed up, is there a way to find only those files and restore them to the thumbdrive?

---

### Post by tea for one on 2012-07-20
Why can you not restore your complete back-up to a free partition, identify the exact files you need and then put them back on your thumb drive?

---

### Post by Mark_in_Hollywood on 2012-07-20
Thanks for the suggestion. I think I may have a better idea and am closing this thread, but not marking it solved.

---

