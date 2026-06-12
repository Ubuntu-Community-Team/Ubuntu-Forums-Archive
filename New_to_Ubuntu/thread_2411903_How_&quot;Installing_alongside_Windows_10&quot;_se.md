---
title: "How &quot;Installing alongside Windows 10&quot; selects the drive"
date: 2019-02-05
forum: New to Ubuntu
---

### Post by jkosonen1 on 2019-02-05
Hello, after struggling quite a bit with making my dual boot work, I did manage to do it. I had trouble because my situation is this: I have my main hard drive, and my secondary hard drive for games (even a 3rd one for media stuff, but that's hardly relevant). In Windows, I created a partition for Linux on my 2nd hard drive, and tried installing into that. Maybe I just sucked at Googleing, but I couldn't find much info about a setup like this. I got into the part where you setup your own partitions for Ubuntu to use, but I got kinda scared cause none of the tutorials/forums posts really seemed to have my situation. A secondary hard drive with partitions already on it, that is.

So, I went back into the Installation selection screen and went with the uppermost option: Install alongside Windows 10. I was hoping the installer would have asked me, on which drive do I want to install Ubuntu on and how much space to give it. I guess it kinda did try to do at least the "where" part, but it certainly wasn't very clear to me at least. Anyway, it does appear, that Ubuntu got installed onto my 2nd hard drive, into the partition I hoped it would. Why is that? Google didn't really give me a clear answer to this. 

Any insight would be much appreciated!

---

### Post by oldfred on 2019-02-05
If you have multiple drives, best to only use Something Else install option.
You can either create partitions during install or create in advance with gparted from live installer.
You cannot create partitions in Windows as it does not create ext4 formatted partitions. 
You cannot install Ubuntu to any Windows type partitions as they do not support Linux ownership & permissions. 

You should use Windows to shrink any NTFS partitions and reboot immediately to run chkdsk on that partition which is required by Windows.
Make sure Windows fast start up is off.

Another choice is to disconnect all drives except drive you want to install Ubuntu onto. Most new systems have settings in UEFI to turn off or hide drives, so you do not have to physically disconnect them

But if Windows is UEFI with gpt partitioning, you need to be sure all drives are gpt also. 
I also prefer to have an ESP on the Ubuntu drive, so it could be made bootable without Windows drive. But if all drives are connected, it will see Windows drive's ESP and install Ubuntu/grub boot loader to a new /EFI/ubuntu folder in the ESP on Windows drive. And selecting to install to sdb or Ubuntu drive in UEFI mode does not work. 

See general UEFI install instructions in link below in my signature.
See 9 steps, but do not skip the backup step.
And see two drive (or more) section  for multiple links with more details on second or external drive installs.

---

### Post by yancek on 2019-02-05
> it certainly wasn't very clear to me at least. Anyway, it does appear, that Ubuntu got installed onto my 2nd hard drive, into the partition I hoped it would.

I would guess that happened because that was the first unallocated space it found.  See the post above on creating partitions for Linux on windows and filesystem types.  Windows filesystems won't work with Linux.

---

### Post by jkosonen1 on 2019-02-05
Thanks a lot for the answers! And indeed, it was empty space that I meant, not a Windows partition. My bad! :)

---

