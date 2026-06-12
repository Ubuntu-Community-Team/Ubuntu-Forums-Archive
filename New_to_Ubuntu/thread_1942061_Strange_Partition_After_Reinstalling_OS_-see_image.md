---
title: "Strange Partition After Reinstalling OS -see image"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by acimi66 on 2012-03-16
So I have just Re-install 11.10.
I thought it all went well BUT when I looked for my "/home" ...it was empty. So I checked Gpart and it shows that my stuff is still on there ( see dev/sda6) but it looks like it's given me an "extended" partiton which it has put "/home" on as well.

Any thoughts on how I can remove the extended partiton?

---

### Post by coffeecat on 2012-03-16
> **acimi66 said:**
> 
Any thoughts on how I can remove the extended partiton?

You don't want to do that. An extended partition is simply a container for logical partitions, in your case sda5 and sda6. It's a way of getting round the 4 primary partition limitation of the mbr partition table. Instead of a primary partition you can have one extended partition which is a container for a number of logicals. I can't remember the limit to the number of logicals, but it is far more than you'll ever need.

---

### Post by acimi66 on 2012-03-16
Oh OK,
but when I go to /home all my docs, my music etc are not there. How can I access them as my /home dir?

---

### Post by jerome1232 on 2012-03-16
I'm assuming /dev/sda6 is your home, you need to get the uuid of sda6, and add an entry to your fstab so that it gets mounted in the correct location.

can you post the output of these two commands so that we can help you construct a correct fstab entry?

```
blkid /dev/sda6
cat /etc/fstab
```

---

### Post by coffeecat on 2012-03-16
According to your screenshot, there are 24.56GiB of data on sda6. You say that your music, data, etc are not there? I wonder if, when you installed, you didn't specify sda6 as the home partition, and the installer has set you up with a standard home folder in your root (sda1) partition, so that your files are not being seen.

I'm just theorising here because we don't have enough information yet. Open a terminal and post the output of these commands:

```
mount
df -h
cat /etc/fstab
```

That's a start, but we might need some more information. I shall be logging off in a few minutes, but I'm sure someone else will help. I'll check the thread in the morning anyway.

**EDIT**: I see I was beaten to it by jerome1232. You'll be in good hands with jerome1232. :)

---

### Post by acimi66 on 2012-03-16
Here you are jerome...Thanks

~$ blkid /dev/sda6

/dev/sda6: UUID="0ce495af-115a-4df6-8d8e-0eb277f1a51a" TYPE="ext4"

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ec459ee8-028c-4b6a-b787-c76c5884b2cb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=326dacb6-482c-4744-9204-70b98164ef6d none            swap    sw              0       0

---

### Post by acimi66 on 2012-03-16
thanks coffeecat...
~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tony/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tony)

tony@tony-Satellite-L650:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  3.2G   15G  19% /
udev                  1.9G  8.0K  1.9G   1% /dev
tmpfs                 766M  856K  765M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.9G  116K  1.9G   1% /run/shm

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ec459ee8-028c-4b6a-b787-c76c5884b2cb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=326dacb6-482c-4744-9204-70b98164ef6d none            swap    sw              0       0

---

### Post by oldfred on 2012-03-16
When you reinstalled you did not tell it to reuse (mount) your existing /home. 

You can reinstall but choose to reuse but be careful not to reformat the existing /home partition.
Or use part of the commands from a move home. You already have the new partition and really just need to add that mount into your fstab.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
See parts near end on preparing fstab for switch. Also has an example fstab entry, but be sure to use ext3 or ext4 to match your actual format of /home.

Then you'll have to edit fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

To see UUID 
sudo blkid

---

### Post by acimi66 on 2012-03-16
Thanks Fred,
I'll have a read of that tutorial and see how much damage I can do.

---

### Post by jerome1232 on 2012-03-16
So all you have to do is add the following to your fstab, once your sure it is working, you'll want to unmount home and remove the old home's files (you'll want to make very, very, very sure you have your real home [COLOR="Red"]unmounted[/COLOR] for that last step or you'll delete your actual files. I'll leave that last part for another post as it's not that important.

Open fstab with gedit

```
gksu gedit
```

Paste this in there, at the bottom, save it.
```
# /home, at /dev/sda6 at the time this entry was added
UUID=0ce495af-115a-4df6-8d8e-0eb277f1a51a /home           ext4    defaults        0       2 
```

Reboot, then we can handle how to get rid of the old residual files lurking behind the mount point.

---

### Post by acimi66 on 2012-03-16
In the guide fred sent me to
this command isn't giving me any result

1.  Duplicate your fstab file: 
sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)

2.  Compare the two files to confirm the backup matches the original: 
cmp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)

Is there something here that needs tweaking?

---

### Post by jerome1232 on 2012-03-16
> **acimi66 said:**
> In the guide fred sent me to
this command isn't giving me any result

1.  Duplicate your fstab file: 
sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)

2.  Compare the two files to confirm the backup matches the original: 
cmp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)

Is there something here that needs tweaking?

No output from those is good, it means the commands succeeded, a little redundant and overly cautious imo (after using cp it's safe to assume the two files are identical)

---

### Post by acimi66 on 2012-03-16
Ha, I so glad no result is actually a result!

Nice instructions.

I changed the file, rebooted and NOW it asked me for my password which it is rejecting. It's the same password as my old user ID, so i don't know whats gone wrong.

I know there is a command line to change it I just need to look for it. I'm signed in as a guest. Home contents are still empty. but I guess we still need to do one more thing?

---

### Post by jerome1232 on 2012-03-16
it didn't get mounted, let's verify the new fstab

```
cat /etc/fstab
```

edit: I included quotes in my previous example, they may have thrown it off, try with my updated post.

---

### Post by oldfred on 2012-03-17
Password is in system not in /home. So you should be using new password from most recent install not old one.

---

### Post by acimi66 on 2012-03-17
Sorry to leave you hanging Jerome. 
I was not able to get back into the system after that last reboot so I simply went back and re-installed and while I was there I assigned the mount to home. Which worked...eventually.

I know it was the long way round but I had nothing to lose (but time) as I had just installed it anyway.

Thank you guys for all your help.
This community is amazing.

---

