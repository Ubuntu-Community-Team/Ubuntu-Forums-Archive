---
title: "LiveUSB - Pre Reinstallation of 12.04 questions"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-06-13
I am about to start a reinstallation of my OS. I have a LiveUSB (netbootin) made about a year ago. I have a backup from about four days ago. I would like to make a backup (using the default Ubuntu backup program named: backup) of my current (yesterday) /home and /mythtv folders. I am in LiveUSB mode as you read this post.

1 - How do I find the now unmounted /home partition? If I see /home does that mean it is mounted during the LiveUSB session and does being mounted affect how "Backup" works. In other words: must I mount the /home, inspect it and then run "Backup" against it or does it have to be unmounted first, before "Backup" can run it?

2 - As I cannot boot the OS, is there a way to get a list of programs, apps, and commands (installed packages) I have installed even though the OS will not boot? I know I have "Aptitude" installed. And some programs for compiling, for one example: checkinstall. I cannot know all the names of all the installed packages and some I have used only once: DeVeDe and other I use so infrequently, I have forgotten they are installed. So, can I use (run or call) Synaptic Package Manager on a corrupted and unmounted OS and make a safe and secure "list"? If "No", is there a way to get this done otherwise?

3 - How can I, as "User" in LiveUSB session save a webpage? I try this and the folder I made is owned by "root" and I cannot save into it from LiveUSB session and I can't change permissions? Nor can I save a webpage to a thumbdrive that I (user:mark) do own!

4 - Why do we backup /home rather than /"user" - in my case my /"user" is: /mark (which name can confuse at times)?

---

### Post by zero2xiii on 2013-06-14
Hay,

Okay currently I can not replicate your set up so I will TRY and assist you from the top of my head.

I assume you have knowledge on how to use the terminal and how to format the output I will request. If not, please have a quick peek here:
[http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446](http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446)

Right let us start addressing the issues:

> 4 - Why do we backup /home rather than /"user" - in my case my /"user" is: /mark (which name can confuse at times)?

This is because /home has all the users' files:
/home/user1; /home/user2; /home/user3; etc.
Thus, backing up the ENTIRE /home partition you update all the users' "home" directories, not just a single user's.

> 3 - How can I, as "User" in LiveUSB session save a webpage? I try this and the folder I made is owned by "root" and I cannot save into it from LiveUSB session and I can't change permissions? Nor can I save a webpage to a thumbdrive that I (user:mark) do own!

You are not being clear WHERE this folder is created, however you can cd to its location in terminal and chown it as follow:
assuming the "folder" is under the current user's desktop directory:
```
cd ~/Desktop
sudo chown -R $(whoami):$(whoami) "./The_website_folder"

```

The ~/ in the above is equal to the current user's home directory: /home/*username*

> 2 - As I cannot boot the OS, is there a way to get a list of programs, apps, and commands (installed packages) I have installed even though the OS will not boot? I know I have "Aptitude" installed. And some programs for compiling, for one example: checkinstall. I cannot know all the names of all the installed packages and some I have used only once: DeVeDe and other I use so infrequently, I have forgotten they are installed. So, can I use (run or call) Synaptic Package Manager on a corrupted and unmounted OS and make a safe and secure "list"? If "No", is there a way to get this done otherwise?

A nice and easy way to do exactly this is found here:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

However for that to work you will need to chroot into the old install, I will now cover how to do that, this is part of the answer to you first question so please read carefully and follow the steps exactly so you can find the relevant information later on again:

Open up a console and do the following, note the **BOLD** parts, as these are the important parts that will differ on your system:
```
sudo fdisk -l | grep "/dev/"
```
this should generate output similar to this:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
/dev/sda1   *          63   150336269    75168103+  83  Linux
/dev/sda2       150336331   156296384     2980027    5  Extended
/dev/sda5       150336333   156296384     2980026   82  Linux swap / Solaris
Disk /dev/sdb: 250.1 GB, 250059350016 bytes
/dev/sdb1   *         187   488392064   244195939    5  Extended
/dev/sdb5       487790592   488368127      288768   82  Linux swap / Solaris
/dev/sdb6             189   390652604   195326208   83  Linux
/dev/sdb7       390652668   487788543    48567938   83  Linux
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
/dev/sdc1              63  1646325134   823162536    7  HPFS/NTFS/exFAT
/dev/sdc2   *  1646325760  1646530559      102400    7  HPFS/NTFS/exFAT
/dev/sdc3      1646530560  1953521663   153495552    7  HPFS/NTFS/exFAT

```

Now let us assume your USB drive is /dev/sda, your other linux install should be in any of the other drives.
Assuming you have a VERY basic set up (not like my multi drive, multi partition on this system), your installation should be /dev/sdb
So let us chroot (change root) into that install:
```
lsblk /dev/**sdb**
```
 sample output:
```
sdb      8:16   0 232,9G  0 disk 
&#9500;&#9472;sdb1   8:17   0     1K  0 part 
&#9500;&#9472;sdb5   8:21   0   282M  0 part [SWAP]
&#9500;&#9472;sdb6   8:22   0 186,3G  0 part /home
&#9492;&#9472;_**sdb7**   8:23   0  46,3G  0 part /_

```
You want the root (/) partition.

Now create a mount point and mount that partition:
```
sudo mkdir /mnt/old_linux
mount /dev/**sdb7** /mnt/old_linux
```

Now you are ready to change to the damaged install, from here on forward you are no longer working on the USB drive, but on the actual install of the linux on your hard drive so please take caution not to do anything other than what you need, and exit cleanly. If your system is damaged on a system level, this will most likely fail, and then it is not possible to find the installed applications.

```
sudo chroot /mnt/old_linux /usr/bin/bash
```

If all goes well, you are now inside the old linux.

Now, do the following:
```
pwd #take note of this location, it should state** /**, just make sure of the path as this is important a little later
sudo dpkg --get-selections > installed-software
cat ./installed-software #this should generate a lot of output.. You will recognize it as an install list

```
If all went well this far you are set:
```
exit #you should now be back to the live environment
cp /mnt/old_linux**/installed-software** ~/Desktop/installed-software
```
The bold should be the same as the output of "pwd" after the chroot command. This should have created a file on your current desktop called "installed-software".

If everything went well this far, congratulations!

> 1 - How do I find the now unmounted /home partition? If I see /home does that mean it is mounted during the LiveUSB session and does being mounted affect how "Backup" works. In other words: must I mount the /home, inspect it and then run "Backup" against it or does it have to be unmounted first, before "Backup" can run it?

/home should be listed when you ran:
```
lsblk /dev/**sdb**
```
If not, it is under the root partition:
/home/*user*
Then you can access it by going to (assuming you did everything exactly as the above):
/mnt/old_linux/home

If not, you can mount it just the root partition above (as in my case I will need to do)
```
~/:~$ lsblk /dev/sdb
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   0 232,9G  0 disk 
&#9500;&#9472;sdb1   8:17   0     1K  0 part 
&#9500;&#9472;sdb5   8:21   0   282M  0 part [SWAP]
&#9500;&#9472;sdb6   8:22   0 186,3G  0 part /home
&#9492;&#9472;sdb7   8:23   0  46,3G  0 part /

```

I will need to do:
```
sudo mkdir /mnt/old_home
sudo mount /dev/sdb6 /mnt/old_home
```

Now I can find my old home directory here:
/mnt/old_home


I hope that all made sence, very good luck, and post all output you are not certain of and ask, rather than screw up the system.

Cheers

---

