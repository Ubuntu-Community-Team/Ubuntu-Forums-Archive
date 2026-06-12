---
title: "Mounting Slave drive issues"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Humphrey_Brogart on 2008-04-23
So I'm fairly new to Ubuntu (and enjoying it!) and I just got a nice new 500GB internal hard drive for storage.  I installed it and set it up to slave.  I'm pretty sure my BIOS detected it.

I did sudo /sbin/fdisk -l

As you can see, I'm new enough that I don't even know how to do the nice terminal print in the forums, but this was the result in the terminal.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13f2275c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


What would my next step be?  I was looking at the fstab instructions and it seems kind of complex. Can someone tell me what my next steps should be in recognizing/mounting this slave drive?

---

### Post by Moop on 2008-04-23
Use Gparted to partition and format your new hdd. You can install Gparted from Synaptic or boot off the live cd which has Gparted integrated.

---

### Post by Tatty on 2008-04-23
It all looks fine, It is labeled as sdb. you need to format your drive now to give it a filesystem to work with.

You can do this in gparted:

```
sudo apt-get install gparted
```

This will then appear in System->Administration->Partition Editor


What do you intend to use your disk for?  Typically Ext3 is the default linux filesystem,  but there are other options dependin on what you need it for.

---

### Post by aparigraha on 2008-04-23
and then have a look here:
[HowTo fstab]("http://ubuntuforums.org/showthread.php?t=283131")

i end up there myself all the time

---

### Post by Humphrey_Brogart on 2008-04-23
I'm planning on using it mainly for storage of my media and hopefully to use as a tester for different linux distros.  I'm not concerned about returning to windows any time soon.  Is there a different file system I should use if I want to test out distros on it or would ext3 be fine?  

Thanks for all the help, I've been working on this a good portion of the day.

---

### Post by aparigraha on 2008-04-23
i would stick to ext3

---

### Post by Humphrey_Brogart on 2008-04-23
Thanks again for all the help, I'm running gparted but I'm not sure what label to use for the new partition.  Is the default msdos alright to use?

I also had another question about making it available to certain users.  Basically I would like to make it accessible for another username (let's say "house") so that my roommates could be able to access my media.  How would I go about this?

---

### Post by aparigraha on 2008-04-23
You can label it anything u like. Maybe "500gb", "storage"... or something like that. Calling it "msdos" wont really make a difference, but since it is not a "Microsoft Disk Operating System", it might make things a bit confusing later on.

---

### Post by Humphrey_Brogart on 2008-04-23
Sorry,I should have specified.  When I go to create the partition it asks for a disklabel.  This seems different then labels because it has preset choices such as "msdos" "amiga" or "bsd"

---

### Post by Moop on 2008-04-23
You want the msdos label.

---

### Post by aparigraha on 2008-04-23
aha, didn't read your post too carefully it seems. :)
go with msdos

---

### Post by aparigraha on 2008-04-23
> **Humphrey_Brogart said:**
> Thanks again for all the help, I'm running gparted but I'm not sure what label to use for the new partition.  Is the default msdos alright to use?

I also had another question about making it available to certain users.  Basically I would like to make it accessible for another username (let's say "house") so that my roommates could be able to access my media.  How would I go about this?

Create more users, and a group called "house". Set permissions to the drive accordingly. [Permissions]("http://www.zzee.com/solutions/linux-permissions.shtml")

And maybe have them ssh/ftps to it?

---

### Post by Humphrey_Brogart on 2008-04-23
I've been reading a bit and it seems pysdm can be used to automatically mount my drive at boot.  Is this correct?  Is fstab the better route to go?

---

### Post by aparigraha on 2008-04-23
can't really say anything about psydm. fstab hasn't failed me yet though... mounts at boot every time :)

try just restarting your machine with the newly formatted drive, and it will hopefully be detected automatically.

---

### Post by Humphrey_Brogart on 2008-04-23
So I restarted and the drive shows up with my other drives.  Two questions though:

1) I must have done something wrong because it says I can't write to the drive.  What can I do about this?  Also, I'm prompted for a password to access it.  Is that normal?  That may be an ubuntu thing that I need to get used to.

2) Can I rename the drive or do I rename the mount point?  Would this create issues?  If I was on my native XP I would change it without much worry but I'm being extra cautious with this.

---

### Post by aparigraha on 2008-04-23
1. U need to set the permissions and perhaps the ownership for the drive. First find its mount point... should be something like /media/sdb1/ , /media/sdc2/ or similar. Then decide which kind of permissions u prefer. Check the Permissions-link posted above. Then you need to set the permissions according to that link. Something like this:

sudo chmod 644 /media/sdb1
or
sudo chmod 755 /media/sdb1

(do you want all users in house to have both read and write capabilities? it's up to u)

you might also want to change ownership of the drive, but it might not be needed.

sudo chown -R USERNAME:USERNAME /media/sdb1
or
sudo chown -R USERNAME:HOUSE /media/sdb1
          (newowner:newgroup)

2. Yes you can rename it, and it should not create issues. You do not need to rename the mountpoint. Do it with the label part in the "How To fstab"-link I posted.

While u are at it, make a backup copy of your fstab. So you know where to restart ;)

sudo cp /etc/fstab /etc/fstab_backup

---

