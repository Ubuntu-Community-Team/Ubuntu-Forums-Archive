---
title: "Multi partition installation help"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-10-11
I have two drives (250 & 320 GB respectively).
My intent is to have a partition scheme that looks like this:

|--------|-----------|---------------------------| Disk1
  300MB * * * 40GB * * * * The rest of the drive
  Boot * * * /(root) * * * * */home 

|----------|--------------------------------------|Disk2
  4GB * * * * * * * * * *The rest
  Swap * * * * * *Media storage & VBox drives

edit:  Sorry for all the stars.  It was the only way to keep the partition descriptions under the right partitions since multiple spaces are condensed!

Creating the installation is no problem, as the installer takes care of all this.  The problem is that, I think I need to make the storage partition on Disk2 mount at boot if I am going to use it to store my media and virtual disks (if I want to use the virtual machines with ease).  How do I make this happen?  Will it happen automatically when I try to use the virtual drive?  How about if I try to play a media file from that partition?

Thanks

JTS

---

### Post by drs305 on 2008-10-11
You can easily make an entry in fstab for the second drive. The entry will depend on the formatting you use. 

If it is going to be an NTFS partition, you can install 'ntfs-config', run it from System Tools, NTFS Configuration Tool, and after you answer a few questions it will set it up as Read/Write and enter the fstab entry automatically.

For an ext3 partition, you would need to create the mountpoint (folder, usually in /media), change the ownership to yourself, and then make the fstab entry, generally along the lines of:
/dev/sdb2 /media/mountpoint ext3  defaults 0 2

For fat32, the procedures are about the same as for ext3 but the fstab line is a bit more complex.

If you need help, once you have formatted the partition, we will need the mountpoint you would like to use and the partition designation (sudo fdisk -l) and if you want to use UUIDs instead of device designations (/dev/sdb2), the results of 'sudo blkid'.

Having the partitions mount on boot are not necessary but can simplify things in the long run.

---

### Post by jimmy the saint on 2008-10-11
Thanks for the response!!  
They will all be ext3.  
Two questions though. 
First - You said it is not neccessary, but saves problems in the long run.  For the uses I laid out, should I just forget about the auto-mount and assume that everything will work?  
 Second - The partitions (on my installation now) show up in media and in nautilus already, but are not mounted.  Do I still need to create a mount point?  I have been using Linux for a year or so now and I'm still confused as to the difference between a drive that shows up, but is not mounted, and a mounted drive!

---

### Post by drs305 on 2008-10-11
As for the second part of your question, the devices always are mounted to a mountpoint, which for all intents are just folders to you and me. So the folders will exist whether or not the device is mounted. They will be empty when the device is not mounted.

I wrote my first response the way I did because it depends on what type of device you are using. Removable devices (external usb drives, thumb drives, etc) are now *supposed* to automatically mount when they are inserted or powered on. This is generally a good way to treat them, but sometimes they won't automount or a user just wants to always have them mounted. One major problem with this is that, since they are removable, their designation (sdf1, sdg1, etc) could change depending on what was plugged in at boot. That is why UUIDs and labels are probably better for removable drives and arguably all partitions.

If your drives are both internal, you need to check your fstab entry and compare it to the fdisk results to see if they are already listed for automounting. If you have toyed with your fstab previously, even external drives may be listed.

To see the fstab entries:
```

cat /etc/fstab

```

To run fdisk (with a small L):
```

sudo fdisk -l

```

---

### Post by jimmy the saint on 2008-10-12
Alright!  I just discovered something that never dawned on my before.  In the installer, you can set partitions to mount at any point you want at startup!  Probably the only one that didn't realize that.  

Now I just have one more question.  The partition is mounted to
/home/me/storage.   It is owned by root, and is not accessible to my user.  If I want to change the owner to me, do I also need to change the group from root?  If so, to what?

Thanks!
JTS

---

### Post by bodhi.zazen on 2008-10-12
> **jimmy the saint said:**
> Alright!  I just discovered something that never dawned on my before.  In the installer, you can set partitions to mount at any point you want at startup!  Probably the only one that didn't realize that.  

Now I just have one more question.  The partition is mounted to
/home/me/storage.   It is owned by root, and is not accessible to my user.  If I want to change the owner to me, do I also need to change the group from root?  If so, to what?

Thanks!
JTS

Ownership and permissions depend on the file system.

From the previous posts, is this an ext3 partition ? If so ;

```
sudo chown me.me /home/me/storage
```

where "me" is your log in name.

---

### Post by jimmy the saint on 2008-10-12
Excellent! Thank you all for your help.  The only thing I had to change was that rather than "me.me"  it needed to be "me:me".  Now to move on to the next issue!!
Thanks guys!

JTS

---

