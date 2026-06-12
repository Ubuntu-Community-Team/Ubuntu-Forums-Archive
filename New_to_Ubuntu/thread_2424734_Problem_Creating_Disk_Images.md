---
title: "Problem Creating Disk Images"
date: 2019-08-13
forum: New to Ubuntu
---

### Post by MrRubik on 2019-08-13
I'm a very new Ubuntu user and i'm working on different backup solutions. I've got my duplicity backups working fine but I also want to periodically take disk images of my 256GB SSD. I've got a 2TB storage drive so I have plenty of space. I want to take a disk image of the 256GB SSD and save it directly to my 2TB storage drive. However, every time I try to do this I get a permission denied error. I am booting into Ubuntu off my flash drive. I've tried with both the 256GB SSD and 2TB storage drives mounted and unmounted and it won't work either way. I was able to take a disk image and storage it on my external drive perfectly fine. I would really like to be able to take these images and put them directly on my storage drive. Can someone please help me with this? Thanks.

---

### Post by rbmorse on 2019-08-13
What method/utility/application are you trying to use to create the disk image?  Also, assuming the storage drive is an internal hard disk mounted during boot via fstab?

---

### Post by MrRubik on 2019-08-13
> **rbmorse said:**
> What method/utility/application are you trying to use to create the disk image?  Also, assuming the storage drive is an internal hard disk mounted during boot via fstab?

I am booting into Ubuntu off my flash drive and then going into the built-in Disks utility. I'm making sure my 256GB drive is unmounted and then clicking the 3 little dots in the top right of the window and choosing "Create Disk Image". Then when it asks me where to store the image, I am choosing my 2TB internal storage drive. The 2TB storage drive is mounted during boot. Thanks.

---

### Post by TheFu on 2019-08-13
backups generally need to be performed with root-privilege.  Also, you probably don't want to write the image to a 2TB drive unless you want to wipe everything on that drive.  Perhaps writing to a partition on the 2TB drive as an image file would make more sense?  Any of the dd-like tools can do that.  I would use ddrescue and pipe the output through gzip to get a compressed .gz image file if I wanted an image.

There are all sorts of problems with image-based backups, but whatever works for you is great.

I've never used "Disks" - I find GUIs confusing for repeatable processes.  Much prefer a script that can be run over and over with the same program, same options, to get the same results.  Then I'd have another tiny script to do the restore, also using the same program, known options, and getting the desired results.  With a GUI, it is so easy to pick the source or target incorrectly at 4am.

---

### Post by MrRubik on 2019-08-13
Yes. I do understand what you are saying. Can you tell me about some of these problems with image-based backups? The reason I want to do an image backup is because I am very new (like 3 days new) to Linux. So I'm playing around with a lot of stuff and if I mess anything up I'd like to just go back to exactly how things were. Does this make sense? If there is a better option for this, please share. Also, what would be the problem of writing my image to my 2TB internal drive? Since it's just 1 file, I don't really see how that wouldn't be a good idea.

---

### Post by yancek on 2019-08-14
If you want to write your disk image to a secondd drive, you need to have root (sudo) privileges to do so as pointed out above.  I'm not familiar with the Disks utility so have no advice on that.

You want to be sure that writing your disk image to another drive does not overwrite anything already on the drive so creating a partition for that specific purpose would probably be a good idea.

---

### Post by GhX6GZMB on 2019-08-14
No reason to make a disk image backup (which will copy every single byte on your drive).
A file image backup is sufficient for what you want to do and much smaller and faster. Check out this thread:
[https://ubuntuforums.org/showthread.php?t=2424669](https://ubuntuforums.org/showthread.php?t=2424669)

---

### Post by TheFu on 2019-08-14
> **baileyhood said:**
> Yes. I do understand what you are saying. Can you tell me about some of these problems with image-based backups? The reason I want to do an image backup is because I am very new (like 3 days new) to Linux. So I'm playing around with a lot of stuff and if I mess anything up I'd like to just go back to exactly how things were. Does this make sense? If there is a better option for this, please share. Also, what would be the problem of writing my image to my 2TB internal drive? Since it's just 1 file, I don't really see how that wouldn't be a good idea.

Drive and partition mean different things. Windows confuses people by using them interchangeably.  That is very unfortunate.  If you clone the entire SSD device ( sda? ) to the 2TB drive (sdb?), then the first 256GB of sdb will be identical to sda - bit-for-bit.  That is what "imaging" means.  That would clone the partition table, everything from sector 0 on to the size.  sdb would report that it is 2TB in size, but all the data on the drive would say I'm 256GB in size.  Coming from Windows, you probably didn't know this was possible.  Unix is very simple deep down.  It will let you do almost anything you ask.  It doesn't know if you are being stupid or a genius, so it let's you decide.

Images are the same size of the source. You can compress them and you can force them to be written to a different device or to a file.  If you ensure that any empty space on the source drive has all zeros, then the compression for the image will be much greater than just getting unallocated, random, left-over, bits.

Images clone everything, so you have an image that will likely only work for 1 specific hardware configuration if there are any proprietary device drivers.  GPU drivers are especially bad, if you need to move to a different computer, but disk controllers and network devices, especially wifi, can be difficult.

You need backups that let you restore to different hardware anyways.  Why bother wasting time and effort making an image/backup that only works with 1 motherboard? Do it right, the first time.  Be more efficient with storage, time, and have 60-180d days of versioned backups you can restore.  Handle crypto-locker malware and file corruption issues that you don't recognize for a month or two.  Eventually, you might want networked-based backups, so be sure to pick a tool that works equally well for local and network backups.

Image backups mean you need to boot from alternate media to create them, so any files not being backed up don't change while the backups are happening, unless you've got some sort of ZFS or LVM snapshot capability.  Don't confuse what most people call "snapshots" with a real, frozen, file system, snapshot. They are very different.  For backups that aren't corrupted, you want a real snapshot as provided by LVM or ZFS.

If you don't backup stuff that is trivially reinstalled, that will save backup storage, time, and later, during the restore, it will get back to a running system that does what you need, with all your programs and settings there much quicker.

Some of my systems need only a 150MB (not a typo) for 60+ days of versioned backups because I only backup things needed to get the system back to the same state. Restore begins with a minimal fresh OS install, which solves all sorts of different machine issues, file system changes, new disk stuff, and GPU changes.  Then I restore system and personal settings, followed by system, service, and personal data.  A new install is 15 min.  The rest takes 15-30 min.  In 45min, I have a system that effectively is the same as the version of the backup files used.    Daily backups for my systems require 3-8 minutes, with a few needing longer.  They are available for use during the backup processing.  All the backups happen automatically, so I know they get done.  Imaging will never be an automatic process.  Imaging will never store 180days of backups for 10-20 systems.  Imaging will never let you easily move from nvidia GPU to Radeon GPU with proprietary drivers or from RAID5 to RAID10 to RAID0 to no RAID at all.
Imaging == lots-o-problems.

That's all I'm saying.  Just trying to lead a horse to water ... so he can fish for himself.

---

### Post by rbmorse on 2019-08-14
That's all very true, and there's much wisdom there.  For those that need that heavy capability. 

Some of us just want to be able to put things back the way they were with a reboot and four or five mouse clicks. You can do that with a disk image.  Horses for courses.

---

### Post by MrRubik on 2019-08-14
I appreciate all the great information and i think I've decided on using Timeshift. I am not familiar enough with Linux yet to mess with many things that don't have a GUI. I'm fine with basic operations and simple bash scripts, but for now I'll try to stick to GUI stuff. I do have a desktop and a laptop, but I want my main backups to be particular to this machine. As for file backup, I keep all that stuff in the cloud anyway, so I'm not particularly worried about losing important files as I can just yank em out of the cloud from any machine. My main objective is just to be able to roll back everything, down to the last setting, if I make a mistake somewhere. I do see what TheFu is saying about taking complete disk images every time. After reading, that does seem somewhat pointless for what I want to do. As long as my understanding about Timeshift is correct, it will take one complete image of my system (not the entire drive bit for bit) and it will take incremental backups from that point on. This sounds like exactly what I am wanting to do. Maybe later on when I start shifting away from GUI, which I plan to do eventually, I'll move to something else. But for now, I think Timeshift and my cloud backups for files are my best options. Thank you all very much for your help. I have learned one very important lesson since the switch to Ubuntu, and that's that I'll never go back to Windows, and I'm seriously disappointed in myself for waiting this long to make the switch. LOL.

---

### Post by GhX6GZMB on 2019-08-15
A tip when using Timeshift:
/root and /home are by default excluded from the backup image. It is a good idea to include them during backup. You can always exclude them again when doing a restore, but then you have the option.

---

### Post by rbmorse on 2019-08-15
I like Timeshift and have found it to be useful for it's stated purpose (recovery from a user induced oops! or a failed/undesired  upgrade), but I don't think it's a very good backup tool.  

If you're going to use Timeshift for backup purposes, I strongly recommend you perform a a test session and actually use it to first backup the system, then restore it to a blank/new storage device.  Backup your user data separately as a hedge against the test failing or producing undesired results as you may need it.  

At a minimum walk yourself through the steps you would have to take if you did it for real. 

In either case, you might be surprised to find what Timeshift does and what it doesn't, and recovering from a data disaster is not the time you want to be surprised.

---

### Post by GhX6GZMB on 2019-08-15
What rbmorse said.
As your installation is quite new with probably little content, I encourage you to make a Timeshift backup to a USB stick and purposely smash your HDD (or SSD, whatever) and then do a restore. Only this will ensure that you can actually do a crash recovery in the future. Remember to include /root and /home.

In a future reality, you'll probably never experience a crash, more likely you'll want to roll back unwanted installations or own unsuccessful system modifications. Ask me how I know...
But this approach will emulate a worst case scenario.

Smash command: sudo rm -r /* (unmount all other drives first)

Then run your live DVD/USB, install Timeshift and do the restore. If this works (and I fully expect it to), you can sleep well at night.

PS: Important: your USB backup storage must be formatted as ext4, otherwise it will not work.

---

