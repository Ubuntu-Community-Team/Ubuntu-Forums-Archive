---
title: "Cant get Virtualbox to access A: drive"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-06-14
I have a USB floppy drive that I cant get VBox to read..It gives a message that it doesnt have permissions for /dev/sdb

[ATTACH]73989[/ATTACH]

[ATTACH]73990[/ATTACH]

I have tried various things, even downloaded v1.6.2 from SUN and got the USB to work.But it wont see the floppy as a USB dev

Anyone got any ideas...I really need to get it working,as I have some older programs that require an A: drive to work...

---

### Post by ajmorris on 2008-06-14
hi there,
do you have permission to that device? Can you mount that block device as a normal user? or does it require root? If you cant mount it as a normal user, can you post the output of sudo ls -l /dev/sdb (when the USB device is plugged in)

AJ

---

### Post by Ducatiboy Stu on 2008-06-14
I can mount it as a user and r/w

[COLOR="Blue"]brw-rw---- 1 root disk 8, 16 2008-06-15 08:11 /dev/sdb[/COLOR]

Some have suggested it is a USB issue, but I tend to think it is more a device permissions issue with Vbox

But I have yet to learn how to do permission changes properly

---

### Post by ajmorris on 2008-06-14
> **Ducatiboy Stu said:**
> I can mount it as a user and r/w

[COLOR=Blue]brw-rw---- 1 root disk 8, 16 2008-06-15 08:11 /dev/sdb[/COLOR]

Some have suggested it is a USB issue, but I tend to think it is more a device permissions issue with Vbox

But I have yet to learn how to do permission changes properly

Well... Vbox should have the same permissions that your user does... and since your user is in the 'disk' group, means you can mount that device.

This will be only temporary as udev dynamically loads devices as they are plugged in etc, and when you reboot, all changes are lost, but try this on the device, and then see what Vbox does:
sudo chmod 777 /dev/sdb

that will change the permissions temporarily on /dev/sdb for all users (root, group, other) to have read write and execute permissions.

AJ

---

### Post by Dr Small on 2008-06-14
Did you add yourself to 'vboxusers' and logout, then log back in?

---

### Post by Ducatiboy Stu on 2008-06-15
> **ajmorris said:**
> Well... 


sudo chmod 777 /dev/sdb

that will change the permissions temporarily on /dev/sdb for all users (root, group, other) to have read write and execute permissions.

AJ

Well..It stopped the initial permissions issue and allowed XP to boot..

But...XP in VB does not see A:\   Just keeps asking to insert disk. The disk in A:\ is formated (DOS) and contains a simple test .exe file.

Having "tempy" solved the permissions issue, now i have to look into the "winduznt" issue of why it wont see A:\


So how do I make the permissions perm for Vbox..?

Yes, I am in Vboxusers grp...

---

