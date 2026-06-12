---
title: "Help with changing permissions on an external drive?"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by jps2012 on 2012-03-25
I'd like to ask for help with changing permissions on an external drive. 

In Terminal (bash) I've typed the following command:                                    chmod 777 /media/JPSBackupDrive1 



The terminal returns: 

                                   
chmod: changing permissions of `/media/JPSBackupDrive1': Read-only file system 



But I KNOW it's a read-only file system. That's why I'm trying to change it. Does anyone know a way around this problem? 



The external was first set up for use on a Mac. I'm now using it on an Ubuntu machine (Lucid 10.4). Some of the directories are allowing me full permissions; others are read only. I'm trying to give myself full permissions for all directories on the drive (and I'm trying to avoid resetting permissions file by file, because there are are thousands of files--mostly image files--I need to access). 



Thanks for your help. 



JPS

---

### Post by matt_symes on 2012-03-25
Hi

Try using sudo.

```
sudo chmod 777 /media/JPSBackupDrive1
```

Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by coffeecat on 2012-03-25
In case matt-symes suggestion does not help...

> **jps2012 said:**
> 
But I KNOW it's a read-only file system. That's why I'm trying to change it. Does anyone know a way around this problem? 


To change permissions on a filesystem with chmod, you need it to be mounted read-write. You can't make a read-only fileystem read-write with chmod. You need to change the mount options. However...

> **jps2012 said:**
> The external was first set up for use on a Mac.

I suspect that the filesystem is the journalled version of HFS+ which can be mounted read-only in Ubuntu. This could be your problem. You need it to be mounted read-write to chmod the directories that are causing you trouble, but you can't mount it read-write. Catch-22. There are ways round this. Just to see if it really is HFS+, post the output of:

```
mount
```

---

### Post by jps2012 on 2012-03-25
I'm wondering if the drive isn't mounted (and I'm also unsure of what "mounted" really means; I see the drive listed in a file browser, and can access some folders and files, but not others). 

So I tried a command I found on the linux.org forum: 
mount -t ntfs -o user /dev/hd* /mnt/whateverNote: I replaced "whatever" with the name of my drive. 

Bash returned the following statement: 

ntfs-3g 2010.3.6 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 1, XATTRS are on, POSIX ACLS are off

So now I'm wondering if "POSIX ACLS are off" is a kind of warning to me, and if that issue is why I can't reset permissions with chmod

Thanks for your help. JPS

---

### Post by jps2012 on 2012-03-25
Matt, thanks for the suggestion. I tried it. Bash returns this: "chmod: changing permissions of `/media/JPSBackupDrive1': Read-only file system" 

Some of the folders within JPSBackupDrive1 are still x'd out. I don't see any change that's taken place in terms of permissions. 

Coffeecat: Thanks for the reply. Here's what "mount" returns (the section referencing my external drive is underlined by me): 

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/oem/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oem)
_/dev/sdb3 on /media/JPSBackupDrive1 type hfsplus (rw,nosuid,nodev,uhelper=udisks)_

That's all goobledygook to me! I'm on my second week using Terminal (and it's starting to get fun, but WOW does it sometimes feel like trying to whistle in Sanskrit)!

---

### Post by chipbuster on 2012-03-25
Due to corruption on large filesystems, the hfsplus module mounts all HFS+ drives as read-only by default.

This page provides more information to mount hfsplus drives read-write. 

[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

Just keep in mind that unjournaled filesystems are much more susceptible to data loss.

---

### Post by coffeecat on 2012-03-25
> **jps2012 said:**
> That's all goobledygook to me! I'm on my second week using Terminal (and it's starting to get fun, but WOW does it sometimes feel like trying to whistle in Sanskrit)!

I'll try to explain. :)

> **chipbuster said:**
> Due to corruption on large filesystems, the hfsplus module mounts all HFS+ drives as read-only by default.

chipbuster is right. The MacOS filesystem HFS+, or rather the journalled version of HFS+, is mounted read only in Ubuntu. However, your output of "mount" reveals something interesting:

> **jps2012 said:**
> 
_/dev/sdb3 on /media/JPSBackupDrive1 type hfsplus ([COLOR="Red"]rw[/COLOR],nosuid,nodev,uhelper=udisks)_

I've highlighted the unexpected bit in red. Your sdb3 HFS+ partition has been mounted read-write - at least that is what mount is telling us. This means that it is probably the non-journalled version of HFS+, so you *should* be able to chmod it from Ubuntu to sort out your permissions problems. But... in your first post you told us about a "read-only" error message, which doesn't fit with the fact that your drive seems to be mounted read-write. Let's put that discrepancy to one side for the time being.

Why unexpected? When you format a drive HFS+ in the MacOS Disk Utility, it defaults to the journalled version of HFS+. You have to select non-journalled if that is what you want.

If the drive is really formatted with non-journalled HFS+, then a slight variation on the command that matt_symes posted should help. Try this with the external drive plugged in and automounted. (By the way it is mounted. If you see folders and files in the file browser, the filesystem is mounted.)

```
sudo chmod -R 777 /media/JPSBackupDrive1
```

Let us know if that helps.

---

### Post by jps2012 on 2012-03-25
Coffeecat: I think that's going to do it! Yessssssssssss! Finally! 

The text is flying past at a gazillion wpm in my terminal, but I think I can see the words "changing file permissions." It's been chewing on the files a couple of minutes. I think when it's done, the permission issues are going to be over. A billion to the nth thanks, Coffeecat.

---

### Post by coffeecat on 2012-03-25
@jps2012, that sounds good, but a word of warning. 777 permissions mean that every file will be marked as executable, which is not ideal, but at least they will be accessible.

Let us know if you have any problems.

---

### Post by jps2012 on 2012-03-25
Arrrrrrrrrrrrrrrrrrgh! Nope. Didn't work. But it did attempt to change the file permissions file by file (thus the text flying past in the terminal for five minutes). My first chmod attempt returned a message that the external drive was read-only. 

The second command I tried "chmod: changing permissions of `/media/JPSBackupDrive1/YardSaleRAW02-07-09/YardSaleRAW020709_053.dng': Read-only file system"

So it's the same kind of rejection of permission, but one that lists a rejection for every file on the drive that was (and still is) read-only.

I'm still stuck. It seems a little odd that some folders on the drive are read-write-execute, and other folders are read-only. If it was a journaling issue, wouldn't that affect _every_ file in the system?

---

### Post by jps2012 on 2012-03-25
BTW, just wanted to note that I AM attempting to do chmod as the root user.

---

### Post by coffeecat on 2012-03-25
> **jps2012 said:**
> 
I'm still stuck. It seems a little odd that some folders on the drive are read-write-execute, and other folders are read-only. If it was a journaling issue, wouldn't that affect _every_ file in the system?

Journalling and permissions are entirely different things.

The filesystem must be the journalled version (which makes more sense) and is being mounted read-only despite the "rw" in the output from mount.

You have two options. Remove the journal in MacOS or run the chmod command from MacOS. Assuming you have access to a Mac, here's how you run the chmod command from MacOS on the drive with the label JPSBackupDrive1. Open a Mac terminal, and:

```
sudo chmod -R 777 /Volumes/JPSBackupDrive1
```

---

### Post by jps2012 on 2012-03-25
Thanks, Coffeecat. I'm not sure how to "Remove the journal in MacOS," but I'll look into that (I imagine it's done with Disk Utilities). Will that cause problems in accessing the files in my Mac OS? 

I thought (because I'm guessing a lot) that maybe if I could set up a new group, and assign rights to that group, I could overcome the permissions issue. 

I tried the "useradd" command (with "jps" as my new group name), as in "useradd -m -g jps user2" 

But that returns this from bash: 

"useradd: group 'jps' does not exist
root@freekbox:/home/oem#"

---

### Post by pdr2esmolbra on 2012-03-25
There's a GUI (get it from software centre) called PySDM that might clarify a few things. Still the man page of mount should have everything in there. 

You didn't try changing the values of /etc/fstab/?
Note that some of these changes might not take place until you restart your computer, so try rebooting between big changes

Cheers

---

### Post by jps2012 on 2012-03-25
OK, I disabled journaling (it WAS journaled) on the external drive in bash, using this command: 

sudo /usr/sbin/diskutil disableJournal /Volumes/MyDisk

Note, the Mac How-To pages say that journaling can be disabled in Disk Utilities by clicking on the drive, then "Info," then click on "Remove Journaling." 

But no such option exists (I'm on OS 10.4; maybe that's an option for 10.5 and later). 

Regarding your comment, PDR, I'm very new to Ubuntu, and the "/etc/fstab/" commands/options are unknown to me. I'll look into them. I'll also check out PySDM. 

After removing the journaling via bash, I gave this command again: 

sudo chmod -R 777 /Volumes/JPSBackupDrive1

The cursor in Terminal dropped down a line, but otherwise has made no response for the past two minutes. Hmmm. Didn't return the prompt. Didn't start scrolling a list of files it was changing permissions for. Hmmm. We'll see what happens.

---

### Post by jps2012 on 2012-03-25
Best news of all: YES! All the read-only permissions are now gone from my external drive (originally set up on OS 10.5). Thanks to a lot of help, from Coffeecat in particular. I've learned a lot today, and have a lot more faith in working from the command line, after getting a lot of good info from you guys (some of which might be women).

I did download pySDM, but don't see how to invoke it, or otherwise open it. Maybe it will appear after a restart. 

I got a warning at one point that I was missing the command "uupdate" 

I tried to install it using the following command: 

sudo apt-get install devscripts

Terminal returned the following:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

Has anyone seen this kind of message? Download directories are locked?

---

### Post by coffeecat on 2012-03-26
> **jps2012 said:**
> 
I did download pySDM, but don't see how to invoke it, or otherwise open it. Maybe it will appear after a restart. 

My advice - don't use it. It is one of several unmaintained pieces of software that are intended to "help" with mounting partitions and devices. They all cause more problems than they solve, judging by threads that appear here. Besides, pysdm would never have helped, nor got over the issue that HFS+ journalled can only be mounted read-only in Linux.

> **jps2012 said:**
> 
I got a warning at one point that I was missing the command "uupdate" 

I tried to install it using the following command: 

sudo apt-get install devscripts

Terminal returned the following:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

Has anyone seen this kind of message? Download directories are locked?

You have a package manager open - either Synaptic, Software Centre or Update Manager. Close it if you see that message when trying to use apt-get. If the problem persists, I suggest you start a new thread.

Now that you have disabled journalling, you can use the chown command from Ubuntu as well as MacOS if you need to. Be aware though that non-journalled filesystems are less easily repaired than journalled ones. Also - the 777 permissions that you have applied make all files executable. This was necessary because you need 777 for the folders and sub-folders to be accessible, but the files themselves only need to be 666. If you want some practice at the command line, you could try chmodding all the files (but not the folders) to 666. :) Have fun!

---

### Post by jps2012 on 2012-03-27
Thanks for the advice, coffeecat. I'll avoid pySDM. And if I get some kind of message saying the download is 'locked,' I'll make sure my package managers and Software Center applications are closed. 

I'm wondering if (on the unjournaled external drive, with permissions set to 777), I can reset files to 666 (as you suggested), then set the drive to journaled again. 

Do you think that would result in the same issue I originally had--that the external drive (initially set up on a Mac) can't be read in Ubuntu? 

I'd like to (as you noted) avoid working long-term on a drive that isn't journaled.

---

### Post by coffeecat on 2012-03-27
What you could do, I suppose, is make sure all the files and folders have permissions which work in Ubuntu for you. You can do this from the GUI in MacOS if you want. Right-click -> Get Info and then you set the permissions at the bottom of the get info window. It would be "everyone" that is important here because your UID and GID (user ID and groupID) are different in Ubuntu and MacOS.

Having got all files with correct permissions, you could then rejournal the filesystem and whenever you add files from MacOS, make sure they are read and writeable for everyone.

---

