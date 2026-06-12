---
title: "Cant create new folder in different drive"
date: 2020-05-09
forum: New to Ubuntu
---

### Post by pigswipe on 2020-05-09
I'm VERY new to Linux, just entering at least an hour ago, and i know nothing of Ubuntu, but i navigated to my other drive that i wanted to make a new folder on, and it was grayed out. I tried other solutions but it didn't make much sense. Can someone help me on this?

---

### Post by Perfect Storm on 2020-05-09
Can you tell more about this drive? Is it an extern drive? Another partition? Is it in your root directory?

---

### Post by ActionParsnip on 2020-05-09
What file system is it? NTFS? Ext4?

---

### Post by yancek on 2020-05-09
All Linux distributions were designed as multi-user systems and a 'normal' user will by default, be allowed read/write access only to the /home/user directory.  If you wand access to other parts of the system, you need to either do it as root (using sudo) or change ownership permissions.  Read through the Ubuntu documentation at the links below to get a more thorough understanding.   The 3rd link below gives a detailed explanation of using sudo.

 [https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TheFu on 2020-05-09
> **pigswipe said:**
> I'm VERY new to Linux, just entering at least an hour ago, and i know nothing of Ubuntu, but i navigated to my other drive that i wanted to make a new folder on, and it was grayed out. I tried other solutions but it didn't make much sense. Can someone help me on this?

First, which release of Ubuntu are you running?  20.04, 18.04, something else? The version matters.

Second, which DE/flavor of Ubuntu are you running?  Gnome3, Mate, KDE, XFCE, LXQT or something else?  This matters so we can understand which programs are on the system, by default. Different flavors install different file managers, for example.

Like many OSes, Ubuntu has been adding more and more default security over time.  Most Unix security revolves around file and directory security.  From the ground up, all Unix-like OSes, including all Ubuntus, are multi-user.  This means that by default, an administrator must setup access to new storage and pro-actively decide which users may have access.

People new to Unix-like systems probably don't think much about file systems. They've never needed to, but in the Unix world, there are probably 50 different file systems, each with specific strengths.  
MS-Windows effectively has 3 file systems: NTFS, FAT32, exFAT.
Most HDDs we buy will come formatted with 1 partition as NTFS.

Unix can access NTFS, but it is NOT the preferred file system for a number of reasons. Mainly because it doesn't support normal Unix file and directory permissions without using complex ACLs.  Most of the time, this means that only one userid can access the NTFS file system at a time because permissions can only be controlled at mount time.

In the last year of so, Canonical has decided to force a new, constrained, software package system onto everyone. These are called "snap packages".  If you use the GUI to install software, it is hard to know which type of packaging is being used.  Normally, that wouldn't matter, except that snap packages only allow users to access and create files under that user's HOME directory.  Extra storage added to a system wouldn't normally be available from a HOME directory.  There are ways around that, but most of those methods are beyond what a beginner can handle without some Unix chops.
To see which packages are installed as snaps, use:
```
snap list
```

The first thing I would do is to change the file system from NTFS to ext4 if the storage will only be used on Linux systems.  Typically, Windows cannot access ext4 file systems directly.  For me, I don't care about Windows. If Windows needs access to storage, I'd setup a network method where the ext4 file system doesn't matter.  With ext4, we get access to users, groups, and complete control over different permissions throughout the file system. NTFS permissions are set for all files and all directories through the mount options. It should be avoided, unless you must, must, must, be able to connect the HDD directly to a Windows computer.  Over the network access is completely different and does not need NTFS. Actually, NTFS makes over the network access a little harder.

Anyway, post the answers to the questions asked above and we'll go from there.

Some light reading:
[LIST]
[*][https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[*][https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[/LIST]
Using ext4 makes the mount stuff easier AND provides faster throughput than NTFS too. File systems make a difference about performance and ease of use.

If you want a more complete knowledge, provided in a better order, with deeper understanding, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

If you just want to point-n-click to get it mounted and are willing to fight with it due to NTFS, someone where should be able to help.

---

### Post by pigswipe on 2020-05-09
> **Artificial Intelligence said:**
> Can you tell more about this drive? Is it an extern drive? Another partition? Is it in your root directory?
Its an external drive.
> **ActionParsnip said:**
> What file system is it? NTFS? Ext4?
When i open the properties file, it says the filesystem type is fuse. Is that what im looking for or am i looking in the wrong place?
> **yancek said:**
> All Linux distributions were designed as multi-user systems and a 'normal' user will by default, be allowed read/write access only to the /home/user directory. If you wand access to other parts of the system, you need to either do it as root (using sudo) or change ownership permissions. Read through the Ubuntu documentation at the links below to get a more thorough understanding. The 3rd link below gives a detailed explanation of using sudo.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
When i go to the properties tab and click permissions, everything is set to create and delete files.
> **TheFu said:**
> First, which release of Ubuntu are you running?  20.04, 18.04, something else? The version matters.

Second, which DE/flavor of Ubuntu are you running?  Gnome3, Mate, KDE, XFCE, LXQT or something else?  This matters so we can understand which programs are on the system, by default. Different flavors install different file managers, for example.

Like many OSes, Ubuntu has been adding more and more default security over time.  Most Unix security revolves around file and directory security.  From the ground up, all Unix-like OSes, including all Ubuntus, are multi-user.  This means that by default, an administrator must setup access to new storage and pro-actively decide which users may have access.

People new to Unix-like systems probably don't think much about file systems. They've never needed to, but in the Unix world, there are probably 50 different file systems, each with specific strengths.  
MS-Windows effectively has 3 file systems: NTFS, FAT32, exFAT.
Most HDDs we buy will come formatted with 1 partition as NTFS.

Unix can access NTFS, but it is NOT the preferred file system for a number of reasons. Mainly because it doesn't support normal Unix file and directory permissions without using complex ACLs.  Most of the time, this means that only one userid can access the NTFS file system at a time because permissions can only be controlled at mount time.

In the last year of so, Canonical has decided to force a new, constrained, software package system onto everyone. These are called "snap packages".  If you use the GUI to install software, it is hard to know which type of packaging is being used.  Normally, that wouldn't matter, except that snap packages only allow users to access and create files under that user's HOME directory.  Extra storage added to a system wouldn't normally be available from a HOME directory.  There are ways around that, but most of those methods are beyond what a beginner can handle without some Unix chops.
To see which packages are installed as snaps, use:
```
snap list
```

The first thing I would do is to change the file system from NTFS to ext4 if the storage will only be used on Linux systems.  Typically, Windows cannot access ext4 file systems directly.  For me, I don't care about Windows. If Windows needs access to storage, I'd setup a network method where the ext4 file system doesn't matter.  With ext4, we get access to users, groups, and complete control over different permissions throughout the file system. NTFS permissions are set for all files and all directories through the mount options. It should be avoided, unless you must, must, must, be able to connect the HDD directly to a Windows computer.  Over the network access is completely different and does not need NTFS. Actually, NTFS makes over the network access a little harder.

Anyway, post the answers to the questions asked above and we'll go from there.

Some light reading:
[LIST]
[*][https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[*][https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[/LIST]
Using ext4 makes the mount stuff easier AND provides faster throughput than NTFS too. File systems make a difference about performance and ease of use.

If you want a more complete knowledge, provided in a better order, with deeper understanding, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

If you just want to point-n-click to get it mounted and are willing to fight with it due to NTFS, someone where should be able to help.
I think I'm running 20.04, since i just installed it yesterday. I have no clue what version it is, i just downloaded it off the main website. How would i go about changing the file system? If it changes anything, i selected to install the minimum package.

---

### Post by TheFu on 2020-05-09
FUSE - means it isn't ext4. It is almost certainly NTFS.  Also, "external" could mean USB, eSATA, Infiniband.  eSATA or Infiniband would be better than USB3.

Anyway, I'd use the gparted tool to check out the storage and reformat as needed. There might be other ways.
**sudo -H gparted** is the exact command I'd use in a terminal.  Then I'd be extremely careful to select the correct drive, then correct partition, then right-click and choose ext4 to format, say "apply" and let that run for 20-90 seconds.Then close that application.  Note the exact device you formatted - probably something like sdc1 or sdd1. You need that for the next step.

The device name may not be either of those examples.  And at every boot, the device name can change so we need to use something that doesn't change with every reboot. The UUID is normally used, so we'll use that.

To add the mount information to the fstab configuration file, we need 2 new pieces of information.
* the UUID - a unique identifier that doesn't change between boots
* the location we want the new file system mounted. That location is just an empty directory, somewhere, anywhere, but there are some smarter places to put it to make life easier today and later.

**UUID:**
We need to get the UUIDs for all the partitions on the system - **sudo blkid** will provide that.  Look for the UUID that relates to the device (sdc1 or sdd1).  If you don't see the device from above in the list, then unplug the USB connection and reconnect it. Wait 10 seconds, then run **sudo blkid** again. The highest letter in the device name sd[a-z]1 should be the newly connected disk that has the partition and ext4 file system.  If you aren't 100% certain, stop and ask for help.

Assuming you got the correct UUID now, Using copy/paste or select/paste is the easy way with the UUID.

What will this storage hold?  Movies, TV, Music, videos, files, something else?  Might you add another disk in 3 yrs? If so, best to start thinking about that today and plan for it. 

For reasons that I won't get into, the mount point should proabably go under /media/files1 or something like that.  /media already exists.  **sudo mkdir -p  /media/files1** will make a directory for the mount.

Now, we just need to put all this information in the fstab file. Run this command: **sudoedit /etc/fstab**
at the bottom of the file, add a new line with this:
```
UUID=2471d686-fde5-4680-a75a-xxyyzz11223344   /media/files1 ext4  auto,user,async,nofail 0 1
```
Replace the the example UUID above with the actual one from your blkid output. That line must be 1 line, not 2 lines. Spacing is only allowed between the places shown. 1 or 50 spaces doesn't matter.  At least 1 is needed.  The *auto....nofail* parts must not, cannot, have any spaces. That part of the options have to be handed over to the mount command unmolested - no spaces allowed.

**sudoedit** is the safest way to edit almost all system files with just 2 exceptions that you will probably never need to touch.  Use sudoedit over other options you see.

We're almost done. 2 more steps.

Mount the storage: **sudo mount -a **
Check that the storage was mounted using the **df -Th** command. Do you see it? If not, we need to figure out why not.

And the last step is to set the owner, group and permissions to whatever you want for the mount point to allow the access by all the users you need to have access.  Probably, the 2 commands you need are:
```
sudo chown $USER:$USER /media/files1
```
and
```
chmod 775 /media/files1
```
The 2nd command doesn't need sudo.  So, you don't need to do anything going forward from here.  At boot, it will be mounted to /media/files1 automatically for your use. The permissions will work to allow your userid full access and others read-only access.  If you need something different, there are changes that can be made, but you'll want to learn about file and directory permissions to accomplish that.

One final statement - never set permissions to 777. Never. That is terrible for security.

---

### Post by oldfred on 2020-05-09
If it is NTFS, you have to make sure Windows fast start up did not set the hibernation bit.
If that is set Ubuntu's NTFS driver will not normally mount it. It can be mounted read only.
That is to prevent damage to the hibernated file system. 

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by pigswipe on 2020-05-10
> **TheFu said:**
> "external" could mean USB, eSATA, Infiniband.  eSATA or Infiniband would be better than USB3
Oh, i think i mistyped that, oops. I dont know much about hardware stuff, but its a drive inside the computer, not external.
> **TheFu said:**
> Anyway, I'd use the gparted tool to check out the storage and reformat as needed.
Would reformatting remove everything on the drive?

sorry for the abundance of questions and my brain not being great at processing things

---

### Post by CelticWarrior on 2020-05-10
> Would reformatting remove everything on the drive?

Yes, definitely.

Again, if it's a NTFS formatted partition we're talking about, and if said drive has been used by Windows (with Fast Startup eneabled, the default state, by the way), regardless of you having or not Windows at the moment, that drive is now "read-only". You can backup all its contents to somewhere else and then reformat it if you want. Otherwise you need to mount it in Windows and then disable Fast Startup and then shutdown.

Also of note is that unless you absolutely need that partition to be shared between Linux and Windows, there's no point in keeping it as NTFS. Linux distros don't have the proper tools for correcting that file system if problems arise (and they will). If using only with Linux then EXT4 is arguably the best choice.

---

### Post by TheFu on 2020-05-10
> **CelticWarrior said:**
> Yes, definitely.

Again, if it's a NTFS formatted partition we're talking about, and if said drive has been used by Windows (with Fast Startup eneabled, the default state, by the way), regardless of you having or not Windows at the moment, that drive is now "read-only". You can backup all its contents to somewhere else and then reformat it if you want. Otherwise you need to mount it in Windows and then disable Fast Startup and then shutdown.

Also of note is that unless you absolutely need that partition to be shared between Linux and Windows, there's no point in keeping it as NTFS. Linux distros don't have the proper tools for correcting that file system if problems arise (and they will). If using only with Linux then EXT4 is arguably the best choice.

Well, reformatting only touches the specific partition, so technically, no, it doesn’t wipe the drive, just the partition selected.  However, new hdds are often shipped with just 1 partition, so 99.9999% of the drive would be wiped due to reformat task.  In the linux world, it is common to have 2-5 or more partitions on a drive. There are a number of reasons for this.

---

### Post by pigswipe on 2020-05-10
Thank you! Ill try to do this in the morning tomorrow, so if any problems arise you can expect them 9 hours from now

---

### Post by pigswipe on 2020-05-11
> **TheFu said:**
> Anyway, I'd use the gparted tool to check out the storage and reformat as needed. There might be other ways.
**sudo -H gparted** is the exact command I'd use in a terminal.  Then I'd be extremely careful to select the correct drive, then correct partition, then right-click and choose ext4 to format, say "apply" and let that run for 20-90 seconds.Then close that application.  Note the exact device you formatted - probably something like sdc1 or sdd1. You need that for the next step.

I open up GParted and i right click on the drive, but most things are greyed out. All i can press is unmount, manage flags, and information. It also boots up with an error saying "Can't have a partition outside the disk!"

---

### Post by TheFu on 2020-05-11
Please do not confuse a "drive" with a "partition".  i suspect that has been happening above.  MS-Windows uses both terms, often interchangeably.  This is incorrect.  On Linux, the difference matters greatly.  i won't be able to help without completely accurate information.

Be certain that you've selected the correct drive.  I&#8217;m assuming there are 2 drives in the machine.  it matters.

---

### Post by pigswipe on 2020-05-12
> **TheFu said:**
> Please do not confuse a "drive" with a "partition".  i suspect that has been happening above.  MS-Windows uses both terms, often interchangeably.  This is incorrect.  On Linux, the difference matters greatly.  i won't be able to help without completely accurate information.

Be certain that you've selected the correct drive.  I’m assuming there are 2 drives in the machine.  it matters.
I certainly dont remember setting up partitions on windows, but i have no clue if there is or not. On linux it says theres one, and theres also like 5 drives in the pc

---

### Post by oldfred on 2020-05-12
Its 5 partitions in the PC.

You cannot use gparted in your install, you have to use live installer's gparted or a gparted live system.
If you have little key icons on the partition that shows it mounted, so you cannot edit it.

You use Windows chkdsk on NTFS partitions and Linux fsck or e2fsck on your ext4 partitions.

Post these from Ubuntu live installer's terminal & paste output here, if longer use code tags. You can easily add code tags with Forum's advanced editor and # icon.

sudo parted -l

---

### Post by pigswipe on 2020-05-13
I listened to the directions on the other posts but instead of using sudo for gparted i just used normal gparted and it worked! Thanks everyone!

---

