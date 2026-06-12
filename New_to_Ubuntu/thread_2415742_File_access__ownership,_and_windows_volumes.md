---
title: "File access / ownership, and windows volumes"
date: 2019-03-30
forum: New to Ubuntu
---

### Post by killgorack on 2019-03-30
I have a couple hard drives I use to keep files for different projects that are separate from any system drive. I have a need to move some stuff around, and would love to do it in a GUI and not the console.

The problem is that I cannot remove delete or affect change on the two drives I need to. It seems I haven't the required access to do so.

Here&#8217;s what I&#8217;ve done so far;
Re mounted the drive with;
```
sudo mount -o remount,uid=1000,gid=1000,rw /dev/sda1
```

I&#8217;ve changed the ownership and access of all the files using various chown/chmod commands. Right clicking within nautilus I can see I am the owner, and have read write access.

[IMG]https://killgorack.com/temp_pics/Screenshot_20190330_172134.png[/IMG]

However

When I try and delete one of the files it looks like it&#8217;s doing exactly what I want, it moves to the trash, and the file disappears from the folder.

A quick &#8220;f5&#8221; and again the file re-appears. Its both in the trash, and its original location. No errors or messages..

I cannot edit any files either it still seems I haven&#8217;t the access.

I totally understand this kind of thing can get some folks like myself into trouble, but it would be nice if this sorta thing was easier to get working.

Drives and files within are from a windows system (which is now kubuntu)

---

### Post by TheFu on 2019-03-30
There is no shortcut to understanding file systems and permissions.

First, only Linux file systems support changing permissions.  Windows NTFS, FAT32, vfat, exfat to not. Those permissions are set at mount time and cannot be changed without modifying the mount.

So, the first question is which file system are these problem files on?

Second, I highly doubt you want to mount sda1 with a userid specified. If it is a Linux native file system, it would be very bad, poor (or deadly) for system security.

I don't use remount often, but mount requires a device and a target directory.

To learn about permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)  But it really takes about 45 minutes with 3 different terminals, 3 different userids and 4+ different groups to mess around with and learn how the owner, groups, and other permissions allow and prevent access.

File systems: [https://manpages.ubuntu.com/manpages/trusty/man5/filesystems.5.html](https://manpages.ubuntu.com/manpages/trusty/man5/filesystems.5.html) - it isn't as simple as most Windows users think.

---

### Post by killgorack on 2019-03-30
Yea I get that, everywhere I go people say its different, I understand. My problem i migrated a couple hard drives that were attached to a windows system and expected them to work right off.

What I've done is;
[LIST]
[*]copied everything from one of the drives to an external.
[*]formatted that hard drive to something line ext4 if I remember correctly
[*]placed everything back after a little modifying access levels (which may be incorrect after I do some reading)
[/LIST]

Now I can move stuff around freely.

I really want it to be easier, I think normal users could be off-put by such things. For these flavors to take more of a hold, there needs to be some improvement for the folks/users who migrate.

Thanks for the links

---

### Post by oldfred on 2019-03-30
Windows uses fast start up. And that sets hibernation flag on all NTFS partitions.
Linux NTFS driver will not mount hibernated  NTFS partitions normally as the hibernation will attempt to restore  to previous condition. You may be able to force mount as read only. 

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by TheFu on 2019-03-31
> **killgorack said:**
> Yea I get that, everywhere I go people say its different, I understand. My problem i migrated a couple hard drives that were attached to a windows system and expected them to work right off.

What I've done is;
[LIST]
[*]copied everything from one of the drives to an external.
[*]formatted that hard drive to something line ext4 if I remember correctly
[*]placed everything back after a little modifying access levels (which may be incorrect after I do some reading)
[/LIST]

Now I can move stuff around freely.

I really want it to be easier, I think normal users could be off-put by such things. For these flavors to take more of a hold, there needs to be some improvement for the folks/users who migrate.

Thanks for the links

People have complained about Unix permissions since 1970.  It is integral to Unix, so that isn't going to change. Many millions and millions of users understand them, so you can too.

As for mounting storage, complain to Microsoft.  THEY changed the rules not to properly close file systems as their default.  Think it began with Win8. Prior to that, there wasn't any issue moving disks around because the OS is supposed to mark them as "closed" when going into a powered off state.  

Going forward, it is important that you know which file system is being used.  Each has different limitations and capabilities, though most of the Unix choices will "just work" almost always for an average user.  There are times when you wouldn't want to use ext4, for example. Or times when some options might be best to add manually to improve performance or lifespan.  If you use SSDs, then there are some file system options and techniques to drastically increase the SSD lifespan.  For example, leave 20% unallocated, unused with an SSD.  That lets those extra 20% be used deep inside the SSD firmware for even more wear levelling.

Unix is hard.  It is like learning a new language.  It can be frustrating because there is so much "new" to be learned.  OTOH, you should see how frustrated kids are when they've only seen Unix and are forced to use Windows.  Exactly the same issue, just backwards.

---

