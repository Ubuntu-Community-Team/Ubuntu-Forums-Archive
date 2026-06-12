---
title: "How do I label an HDD that is on the Desktop?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by neurostu on 2008-09-16
So I just added a couple HDD's to the internals of my computer, I've mounted them exactly where I want them, but they are showing up on my desktop as  **500.1 GB Media **. There are three of them with this exact same label, how can I change the label on the drive?

---

### Post by oilchangeguy on 2008-09-16
> **neurostu said:**
> So I just added a couple HDD's to the internals of my computer, I've mounted them exactly where I want them, but they are showing up on my desktop as  **500.1 GB Media **. There are three of them with this exact same label, how can I change the label on the drive?

try right clicking on the drive. there should be an option to rename it.

---

### Post by Peter Frank on 2008-09-16
I have the same problem. However, the "Rename" option is greyed out so I can't click. Tried running nautilus as root, still didn't help. If a hard disk volume has a label, it will be shown by that name instead of "500G media', however I don't know how to change FAT/NTFS labels under Linux.

---

### Post by drubin on 2008-09-16
> **neurostu said:**
> So I just added a couple HDD's to the internals of my computer, I've mounted them exactly where I want them, but they are showing up on my desktop as  **500.1 GB Media **. There are three of them with this exact same label, how can I change the label on the drive?

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
This worked for me. Has instructions for all formats of drives.

---

### Post by cariboo on 2008-09-16
Depending on how the drive is formatted there are acouple of ways to do it.
for ext3 formatted hard drives

```
sudo e2label <device> <newlabel>
```

and for ntfs you will need to install ntfsprogs

There is a tutorial here:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

This tutorial is for usb drives, but the commands will work on internal drives also.

Jim

---

### Post by drubin on 2008-09-16
> **cariboo907 said:**
> Depending on how the drive is formatted there are acouple of ways to do it.

Just shows how get the tutorial is.

---

### Post by neurostu on 2008-09-17
> **rubinboy said:**
> [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
This worked for me. Has instructions for all formats of drives.

So that tutorial is only for external drives.

It said something about being able to label the drives in the fstab file... Does anybody know how to do this?

What about just removing the drive icons from the desktop. I access the data from the command line mostly anyway.

---

