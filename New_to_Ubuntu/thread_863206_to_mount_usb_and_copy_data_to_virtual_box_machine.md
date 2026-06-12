---
title: "to mount usb and copy data to virtual box machine"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by sirus on 2008-07-18
mounting usb in virtual box
 
im using  storage device so im running ubuntu operating system and virtual box is windows so could u pls show me step by step procedure as yr help would be appreciated.

Best regards
sirus

---

### Post by hyper_ch on 2008-07-18
do you use the OSE version (the one that is in the repos)? If so, then go to the vbox document page, there is a howto on usb. If you downloaded adn installed the precompiled vbox from their site, then USB will be enabled by default.

---

### Post by rockerphil on 2008-07-18
ok, i'm guessing you want to mount the USB device in your virtual Ubuntu install. so with the USB device connected to the machine open up a terminal and run this

sudo fdisk -l

that will display your partition table and each one's label. i know on my machine i've got 2 hard drives, my (in Windows it's calld C:) primary shows up as /dev/sda and me secondary shows up as /dev/sdb. since this is a virtual machine the USB device should show up as /dev/sdb. so once you've found out what the drive label is you need to create a mount point, so i'd run this in terminal

mkdir ~/USB

that will create a folder in your home folder titled USB. once you've got the mount point simply run this code to mount it

sudo mount <drivelabel> ~/USB 

without the <> of course. and that should mount the USB device to the folder you created inside your home folder. i hope this is what you were looking for, much luck,


Phil

---

### Post by sirus on 2008-07-18
Hi gurus out there pls help me out about virtual box as im running ubuntu as my host n windows as in virtual box so please give step by step to mount my usb in virtual box n hw to copy data yr help wud be appreciated.

---

### Post by markjensen on 2008-07-18
Maybe a little clarifcation?

You are booting an Ubuntu system with Virtualbox, right?  And within Virtualbox, you are running a copy of Windows.

When you attach a USB device, you want Windows to see it, instead of just Ubuntu?

---

### Post by Inxsible on 2008-07-18
Also, the title of the thread and the matter within are no where related. Could you use specific titles for your problems !

---

### Post by mlentink on 2008-07-18
I'm assuming you run VirtualBox on Ubuntu (=host) and Windows as a guest within VirtualBox.

Do you use the open source version of VirtualBox or the closed source (equally free) version? Because the OS-version does not support USB, but the closed source version does.

---

### Post by bapoumba on 2008-07-18
Threads merged.

---

### Post by Inxsible on 2008-07-18
Well, now it makes sense as to why the OP was asking for "OSE repos" !!

---

### Post by bapoumba on 2008-07-18
> **Inxsible said:**
> Well, now it makes sense as to why the OP was asking for "OSE repos" !!

Eheh, we should have a "LOL" button ^^

---

