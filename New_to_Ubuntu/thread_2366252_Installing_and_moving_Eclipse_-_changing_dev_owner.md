---
title: "Installing and moving Eclipse - changing dev ownership"
date: 2017-07-15
forum: New to Ubuntu
---

### Post by Vaclav Vasek on 2017-07-15
I hope this post belongs here and not in Eclipse.

I keep running in "security" roadblocks, (probably)  because I really do not understand why they are there in first place if most of them can be bypassed by using "sudo". 


1. I want to move the entire directory structure from Downloads to USB stick. Can’t do because I am not the owner - root is. **Is there a _simple way_ to change device ownership?** I did some search and it got so confusing I just given up. 
2. I have same issue when starting Eclipse from Download - cannot create required Workspace.

---

### Post by TheFu on 2017-07-15
I don't mean to be harsh. 

What do you mean by "dev ownership"?  It isn't clear. I'll assume /dev/ files are what you mean, since that is the most common use on Linux.

Using sudo is often a mistake.  It causes more problems later if you don't understand Unix file and directory permissions.  Ignoring those will lead you to having to reinstall the entire OS.

Device ownership is EXTREMELY important for system security.  All file/directory permissions are, but the permissions for devices always have unexpected security implications for all newbies.  There are many subtle security issues with devices.

Sudo doesn't ignore permissions.  It tells the system that you know what you are doing, even when you do not, and it allows add/change/delete of different files.  To you, sudo seems simple.  Make a new account and try to accomplish the same things.  You cannot.  sudo is restricted for a reason.  

Linux and all Unix-like OSes are multi-user from the core. Never forget that.  Processes are run under different userids and groups to help with security. This is a core idea for Unix security.  Know it. Learn it. Love it.

So ... spend 45 minutes with 5 different userids and 4 groups creating directories and files with every possible permission value.  Mix group membership between these users and try to allow and prevent access to members and non-members.  Make files executable, but not readable. Some will work. Others will not. Why is that? Make them modifiable, but not readable. Huh?  Make them modifiable, but prevent deletion. Try every possible combination. See what they do and don't do. Make some directories that can be shared by everyone in every group AND retain the group across all files in there and anywhere below it.  Seems you are good with limiting access already, but doing it on purpose would be handy to know too.

After doing this, you should have at least 10 "ah-ha" moments.  Oh ... and use all 4 octal positions, not just the normal 3.  Practice with setuid, sticky bit and setgid settings.

Do not use a GUI for any of this.  Use chown, chgrp, chmod and similar commands.

That is your first job.

After all that has been mastered, you won't need help with your question - at least you shouldn't.

On Unix-like systems, which is basically everything that isn't Microsoft or MVS mainframes, permissions work this way.  iOS, OSX, Android - they all follow this model.  So does Linux, AIX, HP-UX, Irix, OSF, Digital Unix, Solaris, SunOS, Mastcomp, and probably 30 other OS families.

There are tutorials for the basics, but nothing, NOTHING, can replace hands on practice.

If you choose NOT to learn this today, you are in for weeks, months, years of frustration.  Just learn it now. Seriously. Do it ASAP, today.  Spend the hour.

One last thing ... if you aren't installing software or modifying system settings in /etc/ then don't use sudo.  Creating users and groups requires sudo (modifies files in /etc/).  So does changing group membership.   Avoid using sudo for any GUI stuff. Only bad things will happen, as you are seeing now.  Every 1 in 100 times, you might need to use sudo with a GUI, but don't use 'sudo program' - use 'sudo -H program' or whatever the GUI program that elevates privileges on your system.  Just know that when setup correctly, sudo should be needed for weekly patching and that's about it.

Here's the history of commands on my laptop with sudo in them;
```
$ history|grep sudo 
  154  sudo apt update
  155  sudo apt upgrade 
  194  sudo apt upgrade
  196  sudo reboot
  206  sudo reboot
  381  sudo apt update
  382  sudo apt upgrade 
  383  sudo apt autoremove
  388  sudo apt purge linux-image-4.4.0-78-generic linux-image-4.4.0-77-generic
  403  sudo nmap -sT 31.111.222.333
  479  sudo -s
  481  sudo reboot
  602  sudo vi /etc/hosts
  628  sudo apt update
  629  sudo apt upgrade
```
That list should provide a guide of typical uses.  Cmd 479 ... well, I needed root for a few commands.  That list was over the last 3+ weeks - I patch weekly.

Mounting permanent storage also needs sudo and LVM commands.

Hope this is helpful.

---

### Post by oldos2er on 2017-07-15
> What do you mean by "dev ownership"? I took that to mean the USB device, as they later mentioned > **Is there a _simple way_ to change device ownership?** not /dev.

@[**[COLOR=#000000]Vaclav Vasek[/COLOR]**]("https://ubuntuforums.org/member.php?u=995191") Could you tell us what file system is on the USB device?

---

### Post by Impavidus on 2017-07-15
The other thing you didn't get (we all had to learn it some day) is that if you want to copy some files to a usb stick, you don't copy them to /dev/whatever. That would just ruin the file system on the usb stick. The thing in /dev/whatever is the raw device, with partition table, inode tables etc. as one big blob of bytes. What you actually want is to mount the usb stick (just plug it in and it should be mounted automatically). The contents of the usb stick should then appear at /media/your_username/usb_drive_name/ or something like that. You can copy your files there, use your file manager to safely remove the usb stick and then unplug it.

---

### Post by TheFu on 2017-07-15
So my brilliant reply isn't all that useful. ;(   Oh well.

The real warning for the OP is that different file systems have different permissions capabilities.  Normally USB flash disks are FAT32 and don't work well with programming files from any Unix system.  Some USB HDDs will have NTFS, which is also not good for Linux programming files.  I only mention this because the OP mentioned eclipse.  If you plan to do programming on Linux, then you need to use Linux/POSIX file systems.  You can backup your programming files to FAT32 or NTFS file systems on USB devices or you can format those devices with a Linux file system like ext4.  Of course, of you do that, then most Windows computers won't have easy access to the files anymore.

How the USB storage was mounted determines which userid has which permissions to it.  That is why 
oldos2er asked about the file system being used.  For non-Linux file systems, the owner and group are set at mount time. No method of chmod will fix it, since chmod doesn't work on non-POSIX file systems like FAT32.

We cannot tell you what to type without more information.  
If you run $ **mount** in a terminal, you'll see which storage is mounted where and what file system is used.  $ **df -h** would be helpful too. The mount output will be ugly, but the df should make a nice table.

Clear as mud?

---

