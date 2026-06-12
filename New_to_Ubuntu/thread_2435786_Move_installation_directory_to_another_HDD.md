---
title: "Move installation directory to another HDD"
date: 2020-01-26
forum: New to Ubuntu
---

### Post by heqro on 2020-01-26
I'm looking forward to installing Ubuntu on a desktop computer with two hard disk drives.

After a long time of having Windows fill the entirety of my (then) only hard disk drive across several previous devices for no reason at all, I came across the idea of having two drives, one, little-sized, just for the OS, and the other for downloading university-related files and videogames. Having previously tried Ubuntu on my single-HDD laptop, I found out that I am never asked where I want to save the software, which is making me hesitate so far about the idea of jumping in to Ubuntu on this device.

Just to clarify, I don't want anything to be installed on the main HDD besides what the OS needs, I would just install whatever I need on this separate HDD.

---

### Post by Impavidus on 2020-01-26
You can spread your files over multiple drives, or rather partitions. There may be more than one partition on a drive. On Linux one of those partitions contains the root filesystem. The filesystems on all other partitions get mounted at a directory somewhere in the filesystem, so that all files and directories within that directory, called the mountpoint, get stored in the filesystem of that partition. So if you put your root filesystem on the small drive and mount your big drive at /home, all files you store in /home end up on the big drive. So, in contrast to Windows, you don't choose a partition where something gets stored; you choose a directory and in your /etc/fstab you configure which directory corresponds to which partition.

Files belonging to your software usually get stored sorted by function, not by application it belongs to. Most executables are stored in /usr/bin, most shared libraries in /usr/lib, data files in /usr/share, configuration files in /etc. For applications installed using the package manager (and that should be at least 99% of all applications on your computer), you don't have any control over the directories where it gets stored. There's also no clear distinction between the operating system and applications. Stuff installed in some other way should end up in /opt or /usr/local. User files, and all software that's not system-wide installed, ends up in /home/username.

There are a few applications that store a huge amount of data in /usr/share (a few games come to mind), but if you don't install any of those, all your software should fit in 20GB. So I don't think you've anything to worry about.

Let go your Windows mindset.

---

### Post by vanadium on 2020-01-26
Linux allows you to use the hard drives anyway you want. To make it simple, the installer by default will either use the entire drive or  free space reclaimed from a Windows partition or existing already (in case of dual boot) for installation of the system. Nowadays, a single partition is used containing everything. Swap memory is now implemented with a swap file on the system partition instead of through a dedicated swap partition.

If, in the installer, you choose "Something Else", then you can manually partition and indicate which parts of the system should be installed on which partition.

You just want your system files on one partition, and you will store your data essentially on another HD. By far the easiest approach is to do a default Ubuntu install on your separate HDD. That will in first instance put everything on that separate HDD. However, in linux, it is very easy to change the storage locations to other drives.

1) You must make sure that that other storage location is automatically mounted during startup. That means that the other storage location (your big drive where you store your data) should be included in `/etc/fstab`.

2) Then, you can redirect data folders in your home folder (i.e., Documents, Downloads, Pictures, ...)  to specific folders on your large drive. There are two ways to do this:

a) Easiest way: using symbolic links. Remove the Documents, Downloads, Pictures, ... folders and replace them by identically named symbolic links that point to folders on your big drives. For practical purposes, a symbolic link behaves identically to a real folder to the user. No root privileges needed here (of course, you need to have user rights for the large drive).

b) A bit more difficult, but "deeper" integrated into your system: use "mount bind". These are additional lines in your /etc/fstab that mounts another folder, possibly residing on a different partition, over an existing folder. 

With this setup, all system software goes automatically to the small drive where the system partition resides. Also user configuration data stays on that volume: that resides in hidden folders in your home folder. Your user data remains transparently accessible as before, but lives on the large drive.

Edit: Impavidus was faster than me and suggested to mount your entire /home partition to the big drive. This is another possibility provided that also the big partition is formatted with a native linux file system that supports linux permissions. In is not clear if you dual boot with Windows, but if you do, you will need to keep the partitions of your big drive in ntfs, otherwise they won't be accessible for Windows. And then, you should not put your entire /home there, but only the data.

---

### Post by oldfred on 2020-01-26
I use linking, so a folder in another partition is linked into /home and looks like it is in /home.

I generally suggest a new user just use a separate /home and that can be on another drive. That is easier as the installer creates mount point in fstab and gives ownership and permissions so you can use it. 
If you create your own data partition then you have to create it all yourself.

Back with XP, I had two data partitions, one NTFS for any data I wanted to share with XP and another that was Linux format that Windows could not see. Since I shut down Windows years ago, all my data is now in a Linux formatted data partition.

---

