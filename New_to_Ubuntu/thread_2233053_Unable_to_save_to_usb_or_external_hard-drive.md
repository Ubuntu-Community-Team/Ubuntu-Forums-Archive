---
title: "Unable to save to usb or external hard-drive"
date: 2014-07-06
forum: New to Ubuntu
---

### Post by eternity*7 on 2014-07-06
The error message says that the file does not exist when I try to save a document to a usb or photos to an external hard-drive.

---

### Post by Jonor on 2014-07-06
Has the external drive mounted on your filesystem, i am finding a lot of stuff is reluctant to auto-mount using Ubuntu Gnome 14.04.
Try navigating to your destination folder with a file browser.

---

### Post by yancek on 2014-07-06
It also would be useful to know how you are trying to copy.  Moving in a file manager, drag and drop, from a terminal?

---

### Post by eternity*7 on 2014-07-07
Our computer is divided with Ubuntu on one side and Windows on the other. There is no problem saving to a usb or external hard drive on the windows side.
When trying to save a document to a usb using OpenOffice and Ubuntu I am clicking on Save as and finding the usb in the list of places to save to.

The external hard drive issue is when I am trying to save photos from Picaso using the export option. It brings up a browse option and I am selecting the external drive.

---

### Post by yancek on 2014-07-07
I could understand that you would be unable to save a file in the manner you describer due to permissions issues.  If you are trying to same as a normal user and the permissions have not been changed from the default that would be a problem.  Since you indicate that is not the problem but rather that it is a "file does not exist" error, that makes no sense at all since you are saving the file from inside the file or in the Picasa, saving a file from inside that program.  I must be missing something here.

---

### Post by eternity*7 on 2014-07-07
Disaster- realized was still running 10.4 so of course decided an upgrade might be the solution. Now there is a major melt-down. Did the upgrade from 10.4 to 12.4 and when starting up the computer get the message that can't find the disk / drive. Then if skip this next message can't find disk tmp drive. Skipping this then just boots me out.
Currently at work (lunch break) and hoping when I get home the fairies have magically fixed it. Common sense tells me that won't happen so any miracle cures that a Ubuntu user with beginner level tech skills can use would be greatly appreciated. HELP!!!!!

---

### Post by yancek on 2014-07-07
The first step before beginning an upgrade is to do a backup of any essential data.  I've done several upgrades without problems but have also read numerous posts where people did have problems.  It is usually better as well as faster to backup data and do a new install.  Could you post the exact error you get on boot?

In regard to your initial problem, you haven't indicated what filesystem is on the external hard drive partition but I would guess it is ntfs.

---

### Post by slooksterpsv on 2014-07-08
Lots of stuff that needs to be answered. Let's start with the first question.

Did you ever get your system up and running? If it's not working, hard to troubleshoot? If not, create a new thread, best to do one topic per thread.
What filesystem, as has been asked, is the external?
Are you able to drag and drop files to the drive?
When the drive is connected, and you can browse the files on it, open up a terminal and type in the following:

```

mount

```

You should get text like so, copy and paste it into a code tag here:

```

shawn@shawn-Satellite-C75D-A:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda4 on /media/shawn/TI10675800F type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /boot/efi type vfat (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=shawn)

```

We'll go from there if we get some of those answers, as they'll help.

I know OpenOffice/LibreOffice had a bug where if you tried to overwrite a file, same name, even if you opened it, it won't save, it'll give you an error. The Picasa, not sure.

---

### Post by eternity*7 on 2014-07-08
Unfortunately the back up idea was a problem when we couldn't export files to the external hard drive or USB.
the external hard drive is a maxtor and It isn't partitioned. The computer is partitioned but I don't know more than that.

The message is " The disk drive for / is not ready yet or not present."
Continue to wait, or Press S to skip mounting or M for manual recovery"

if I wait (overnight) nothing happens. If I press S then get similar message but it is the tmp disk drive that is not ready or can't be found. Selecting Skip then boots me out completely.

pressing M gets as far as:
modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-57-generic/kernel/drivers/crypto/padlock-sha.ko) : No such device
This means nothing to me though of corse the words fatal and error worry me!

---

### Post by eternity*7 on 2014-07-08
Have added more info above but will also start a new thread as no, I have not been able to get back up and running.

---

### Post by yancek on 2014-07-08
> the external hard drive is a maxtor and It isn't partitioned. The computer is partitioned but I don't know more than that.


You can get that information by using a command similar to the one below from an Ubuntu Live media (DVD/flash):

sudo parted /dev/sdb print all

That would be if you external drive is sdb.  You make no mention of how many drives you actually have so that is just a guess.  New drives often come formatted ntfs.  I would not expect that if you had no partition or filesystem on it you would be able to use it, even from windows but I'm not expert.  That could be the reason you are getting the disk is not ready message.  I will add that I sometimes get that message on Ubuntu for data partitions on the same or other drives but hitting the 'S' always continues the boot for me.

> This means nothing to me though of corse the words fatal and error worry me! 		

As they should.  The work 'crypto' interest me.  Is the external drive encrypted?  from windows?

---

