---
title: "USB Stick has Read Only Permissions"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by cheesey_toastie on 2008-06-18
Hi,

I had problems with my USB stick but managed to resolve them (from memory following some hack by adding a space to the mount command if that makes sense).  I've since upgraded to Hardy and now I can only browse the contents of the stick.  

I've tried a few chmod commands but can't get anything to work.  A sudo rm allows me to remove files so I know it's permissions!

I tried launching nautilus in sudo and I can delete and add files.  When I try and change the permissions and I get the error saying I'm not the owner.  

Any ideas?

Excuse my permissions ignorance!

CT

---

### Post by dracayr on 2008-06-18
Since NTFS doesn't support owners, the whole stick must have an owner. The owner is the mounting user. If this was a hard disk, you would only have to edit your /etc/fstab, but with automount, I have no Idea. However, if you find a possibility to use an option in auto-mount, this is the option you need:

```
umask=000
```

dracayr

---

### Post by BlackDragonBE on 2008-06-18
I usually do a
sudo nautilus
then using the root nautilus I click on the properties of the USB stick, and make me (your name) the owner.
Then just close the root nautilus or the terminal you started it in and try to access the usb drive. 
Works for me, and you only need to do this once as far as I remember.

---

### Post by cheesey_toastie on 2008-06-18
> **BlackDragonBE said:**
> I usually do a
sudo nautilus
then using the root nautilus I click on the properties of the USB stick, and make me (your name) the owner.
Then just close the root nautilus or the terminal you started it in and try to access the usb drive. 
Works for me, and you only need to do this once as far as I remember.

Tried this... and get an error
Sorry, couldn't change the owner of "USBDISKPRO": Error setting owner: Operation not permitted

---

### Post by cariboo on 2008-06-18
You could also change the permission on /media/USBDISKPRO using this method:

```
sudo chmod 777 /media/USBDISKPRO
```

I don't recommend it but it does work.

Jim

---

### Post by Toadmund on 2008-06-18
I had that problem once and if I can recall, my brother said it had to do with the partition being mounted as NTFS, I think we switched it to Fat32 or ext.
(don't know how he knew that?)
Then the USB stick worked with full permissions.

We used the Gnome partition manager.

Perhaps someone else can clarify this further.

---

### Post by amaroKer on 2008-06-18
Whenever I have any problem with a USB key, I just open GNOME Partition Editor (gparted), and reformat the key to FAT32.  You shouldn't have any problems with that.  See my sig for permissions help.

---

### Post by Toadmund on 2008-06-18
Yes, I think I remember now, the USB stick had it's own partition and that's what had to be formatted.
I just checked, it's actually formatted as Fat 16.

---

### Post by amaroKer on 2008-06-19
Most keys come pre-formatted FAT16, in my experience.  Probably to somehow maximize the use of the memory, but it is incompatible with most devices (ie USB enabled DivX players) so I always format FAT32.

---

### Post by kansasnoob on 2008-06-19
I've had excellent luck with ntfsprogs (available in synaptic) even with encrypted ntfs files.

I always install:

ntfs-config
ntfsprogs

and either:

usbmount

or:

pmount and
hal

The pmount + hal option tends to create a desktop ico everytime you plug in a device but I personally prefer usbmount.

Anyway, this seems to cure my internal and external drive problems for the most part.

---

### Post by cheesey_toastie on 2008-07-01
> **amaroKer said:**
> Whenever I have any problem with a USB key, I just open GNOME Partition Editor (gparted), and reformat the key to FAT32.  You shouldn't have any problems with that.  See my sig for permissions help.

Absolutley bob on!  Thanks!   Gparted seems very useful - newbies be careful - you have to Unmount your device before you can work with it - check the disk size before you do anything though!.

---

