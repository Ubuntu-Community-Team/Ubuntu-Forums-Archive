---
title: "Trying to do that thing with the fstab."
date: 2013-11-02
forum: New to Ubuntu
---

### Post by jonpon on 2013-11-02
My laptop boots to my sdcard (sdb) I'd like it to mount the hard drive (sda) on start up but i cant get the wording queit right.
Here's my fstab file the bit at the bottom is the drive sda

Thanks.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=87b1444b-c3d4-4ab2-87ae-1c003a19fe7a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63101164-be2e-413b-94ea-ba43f599dd23 none            swap    sw              0       0
#The next line is the problem, I'm mounting the sda for more space but it just isn't working.
UUID="22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee sda1   ext3     0   2

---

### Post by oldos2er on 2013-11-02
> **jonpon said:**
> UUID="22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee sda1   ext3     0   2

Remove the quote marks. You need a mount point for /dev/sda1, not just sda1. Maybe /media/sda1 ? ```
sudo mkdir -p /media/sda1
``` so your line in /etc/fstab would look like ```
UUID=22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee /media/sda1   ext3     0   2
```

---

### Post by drmrgd on 2013-11-02
You've not listed a mount point for the drive to mount to.  You need something like this:

```

# Change 'mount_point' to match an actual directory
UUID=22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee     /media/mount_point      ext3     0     2

```

If you're using the UUID for the drive, you don't need to list the partition name too.  So, you have to remove the 'sda1' part.  Instead of that, you list the actual place you want to mount the drive, which is commonly in /media.  So, make a directory in /media (you'll need elevated privileges to make the directory):

```

sudo mkdir /media/mount_point  #call the mount point whatever you like

```

Then, change the ownership of the mount point so that you can rw to it:

```

sudo chown $USER:$USER /media/mount_point

```

Then, you should be all set.

---

### Post by jonpon on 2013-11-02
Thanks for your help guys, 
but I'm still having problems...

this is how it looks now but something is still wrong
```
UUID=22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee /media/sda1   ext3     0   2
```

---

### Post by deadflowr on 2013-11-02
> **jonpon said:**
> Thanks for your help guys, 
but I'm still having problems...

this is how it looks now but something is still wrong
```
UUID=22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee /media/sda1   ext3     0   2
```

What exactly is wrong?
If you open up the file manager and navigate to media, and open it, is sda1 listed? 
And when you open that are the files that where in that partition there?

---

### Post by Impavidus on 2013-11-02
Does the mountpoint exist? You need an empty directory named /media/sda1. You can use any name, as long as the empty directory has the path mentioned in your fstab. A somewhat more descriptive name may be easier. Also, the new fstab will take effect after rebooting (or after you call mountall).

---

### Post by jonpon on 2013-11-02
On startup I get an error that it can't mount. When I navigate to the file /media/sda1 it's there but empty. If I try to open the drive from the menu it says I dont have permission.

---

### Post by drmrgd on 2013-11-02
Two things:

Double check the UUID of that drive.  You can run this to get the UUID of your drive:

```

sudo blkid

```

Second, see my post above about permissions.  Since /media is owned by root, you need elevated perms to create the directory, which will then cause it be owned by root, and you won't have permissions on it.  So, you then need to change the ownership of with with the 'chown' command as I show you above.

Edit:
Just thought of something else, double check that the filesystem type you're requesting is correct.  What is the result of: 

```

mount

```

---

### Post by deadflowr on 2013-11-02
Post the output of 
```
sudo blkid
```
to verify that the UUID and file system type are correct.

Edit: Me be ninja'd

---

### Post by jonpon on 2013-11-02
Here are the results from blkid and mount

```
jonpon@E1222 ~ $ sudo blkid
[sudo] password for jonpon: 
/dev/sda1: LABEL="Android-x86" UUID="22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="bd461586-441f-4e02-a397-2b5558b4a8b2" TYPE="swap" 
/dev/sda6: UUID="4fe32ffa-ff41-4268-bdf5-01a86992b0db" TYPE="ext4" 
/dev/sdb1: UUID="87b1444b-c3d4-4ab2-87ae-1c003a19fe7a" TYPE="ext4" 
/dev/sdb5: UUID="63101164-be2e-413b-94ea-ba43f599dd23" TYPE="swap" 

```

```
jonpon@E1222 ~ $ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jonpon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jonpon)
jonpon@E1222 ~ $ 


```

---

### Post by jonpon on 2013-11-02
What do the 2 numbers mean at the end of the line? ( 0   2)

```
UUID=22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee /media/sda1   ext3     0   2
```

---

### Post by deadflowr on 2013-11-02
> **jonpon said:**
> What do the 2 numbers mean at the end of the line? ( 0   2)

```
UUID=22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee /media/sda1   ext3     0   2
```

Like you, I'm still stumped on the mounting problem.
But to this I'll answer.

The first 0 is for the dump command.
The dump command is for backing up the partition/drive.
0 means that the function is disabled.

The 2 is the setting for the fsck command that will be run.
0 is disable, then 1 is first, and then 2 is second and everything after the first.
So if you look at the partition that loads the system it should have the number as 1, this means it will be checked first.
The one with 2 will be checked next, and so on.

Here
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Also, you can see if automount per user mounts the partition
[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28%28AutomaticallyMountPartitions%29%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28%28AutomaticallyMountPartitions%29%29)
Don't know how helpful that can be, but it's something to look over.
Enjoy

---

### Post by drmrgd on 2013-11-02
Not sure what's going on.  The fstab entry from above looks correct to me, and the UUID and filesystem type does match based on what you posted.  Maybe there's something else wrong in your fstab file as a result of adding the new drive?  Maybe post the full fstab file here.

With regard to your question, the first number '0' refers to backup utility Dump.  I don't know a heck of a lot about it, but I do know it's usually disabled (set to 0).  The second number refers to the order that the drive is checked for errors by fsck.  Usually a root partition is set to 1 and the rest are set to 2, unless you don't want them checked at all, in which case you'd set it to 0. 

More info on fstab can be found here:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Edit: 
Now I got ninja'd! :)

---

### Post by mcduck on 2013-11-02
Maybe you could try adding the default mount options, as the current fstab line doesn't have anything.

```
UUID=22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee /media/sda1   ext3  defaults   0   2
```

...and if even that fails to work, it might me a good idea to try mounting the drive manually from a terminal using the same options in case you get any helpful error message that could explain what's causign the problem.

---

### Post by drmrgd on 2013-11-02
> **mcduck said:**
> Maybe you could try adding the default mount options, as the current fstab line doesn't have anything.

```
UUID=22f9a2fc-30e7-4bd7-87d1-e8e46b3687ee /media/sda1   ext3  defaults   0   2
```

...and if even that fails to work, it might me a good idea to try mounting the drive manually from a terminal using the same options in case you get any helpful error message that could explain what's causign the problem.

Great call!  I totally skipped over the mount options part of the entry.  Also, great idea trying to mount it manually first and then just adding the working mount command to fstab.  Nice tips!  :)

---

### Post by steeldriver on 2013-11-02
... there may also be some useful diagnostic information about why the mount failed on boot in dmesg e.g.

```
dmesg | grep 'mount'
```

or

```
dmesg | grep '/dev/sda1'
```

---

