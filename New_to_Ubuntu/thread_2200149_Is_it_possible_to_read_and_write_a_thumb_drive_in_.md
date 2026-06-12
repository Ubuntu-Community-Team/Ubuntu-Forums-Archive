---
title: "Is it possible to read and write a thumb drive in Unity and windows7?"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by redkilgore on 2014-01-17
I just need to transfer files _both ways_ between 13.10 and various windows machines via a usb drive. I can't install ext file support on every win box I touch, and I am not going to spend twenty minutes at term everytime I need to move a file from my linux laptop to a fat16 (or 32 or ntfs) thumb drive.

I know windows files are read only by default in 13.10 / Unity (Makes a lot of sense for the hard drive on a dual boot system, but removable media, really?)

Maybe the question should be "How can I make windows files / volumes permissions resettable in the Unity properties - permissions tab?

---

### Post by bab1 on 2014-01-17
> **redkilgore said:**
> I just need to transfer files _both ways_ between 13.10 and various windows machines via a usb drive. I can't install ext file support on every win box I touch, and I am not going to spend twenty minutes at term everytime I need to move a file from my linux laptop to a fat16 (or 32 or ntfs) thumb drive.

I know windows files are read only by default in 13.10 / Unity (Makes a lot of sense for the hard drive on a dual boot system, but removable media, really?)

Maybe the question should be "How can I make windows files / volumes permissions resettable in the Unity properties - permissions tab?

By default USB thumb drives are FAT32 formatted.  Ubuntu can read and write to FAT32, just as windows can.  If the thumb drive is auto-mounted upon insertion, the loged in user is the owner of the files on the drive.  File permissions are set at mount time.

What is your specific problem?

---

### Post by buzzingrobot on 2014-01-17
Copying files on Linux to a mounted USB stick can hardly take 20 minutes, in a file manager or using the shell. Don't forget to run sync.

Permissions can be adjusted in Files via a right click on a file, under "Properties".

---

### Post by redkilgore on 2014-01-17
This was posted under[ Absolute Beginners Section]("http://ubuntuforums.org/forumdisplay.php?f=326") so yes, for me, it has taken longer than 20 minutes, and isn't reliable.

I guess BAB1 hasn't actually tried this in Unity. Default is read only.

The permissions tab is there, the choises drop down, but nothing ever changes.

If there is a button a switch, or command that would enable the permissions to change, that would solve it.

---

### Post by buzzingrobot on 2014-01-17
> **redkilgore said:**
> This was posted under[ Absolute Beginners Section]("http://ubuntuforums.org/forumdisplay.php?f=326") so yes, for me, it has taken longer than 20 minutes, and isn't reliable.

Ah, sorry, forgot where I was.

"Sync" is terminal command that flushes data to a drive. Data is very often buffered to RAM during a file operation because it speeds the overall process. When a USB stick is involved, the copy operation can appear to take only a few seconds when the data has only been buffered to RAM, not completely written to the USB stick..  Normally, with a an ordinary unremovable drive, this is not an issue because the file system is updated and will find the right data.   However, when a USB stick is removed from a machine, it loses access to the file system and any buffered data.  So, to ensure that all the copied files are physically written to the usb stick, run sync.

I

---

### Post by redkilgore on 2014-01-17
Sync sounds like a good way to check, but I'm not getting that far. I can format a thumb drive, but not write to it. Read only and permission won't change. Works great to bring things to the Ubuntu system, but I can't take anything from it to a windows system. email, and cloud servers are not practical for systems without internet acess, or large files.

---

### Post by bab1 on 2014-01-17
> **redkilgore said:**
> I guess BAB1 hasn't actually tried this in Unity. Default is read only.

I have 3 Unity machines sitting right in front of me.  The default is certainly NOT read only.

Here is just one thumb drive and it's permissions```
drwx------ 13 bab bab 8.0K Dec 31  1969 San_Disk
```...note the rwx stands for read, write and eXecute.

---

### Post by buzzingrobot on 2014-01-17
> **redkilgore said:**
>  I can format a thumb drive, but not write to it.

When I format a USB drive in Ubuntu, and/or attach it later, it is mounted in the "/media/<my_user_name>" directory. ("Mount" is ancient Unix/linux jargon for making the file system aware of the drive and mapping it to a directory. E.g., if a drive is mounted on /foobar. then all the files in the drive will appear to be in /foobar.)

So, if my username is "buzzingrobot", and my /home directory is "/home/buzzingrobot", when I insert a USB stick, Ubuntu autotmatically mounts it to /media/buzzingrobot.  I can then access and manipulate files there using the filemanager.

I don't have Windows, so I don't know what happens in the other direction.

[I should add that I've found thumb drives to be frustratingly flaky devices.]

---

### Post by king.of.random on 2014-01-17
I can verify bab1's post in that my unity desktop can read and write to usb thumb drive as user. It is also formatted to fat32. Are the permissions set to root? as this would obviously cause your issue but then again you should get an error message right away.... Could the drive be corrupted? Have you tried a different drive and a different usb port? If you can get your data off in windows try reformatting it and copying the data back over.

---

### Post by redkilgore on 2014-01-17
I've tried several drives, same. tried a different usb port, just to be safe, opposite side, still the same. I'm trying to make this work with the mouse, I don't hate the command line, just the keyboard. I start at "Files" file manager, right click on the drive for properties, go to permissions tab, Owner is "Me" Access "Create and Delete" Group and others wont change, nor will access. Change Permisssions for Enclosed Files wont accept changes.

Any file I drag to the drive, or right click and move to or copy to, gets me the same read only message. Mount cmd shows RW still wont work in the DE.

---

### Post by redkilgore on 2014-01-17
Starting to think this may be a Unity version problem, don't know which I have, assume it's 7.1.1 as I have updated 13.10 this week. (Built in update)

---

### Post by fosterD on 2014-01-17
By default, usb should be mounted with read and write permissions, unless your system has some issues.
May be try to tests
1- Create a file by using command line
```
touch /media/<your-usb-directory>
```

2- Verify how the usb is mounted
```
mount | grep media
```

3- Remount the usb
```
sudo mount -t <fs-type> -o rw,remount <usb-partition> <mount-directory>

for example:
sudo mount -t vfat -o rw,remount /dev/sdd /media/my-usb
```

I think these should give you some ideas

---

### Post by mc4man on 2014-01-17
The most typical reason one can't write to FAT or NTFS formatted  removable media is that they where improperly removed in Windows & are then mounted ro (read-only) in Ubuntu
The fact you can't change 'permissions' from properties window is meaningless, those filesystems don't support permissions
Has absolutely nothing to do with unity

---

### Post by redkilgore on 2014-01-17
Does this tell you anything?

red@nx9420:~$ mount | grep media
/dev/sdb1 on /media/red/Purple type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
red@nx9420:~$

couldn't get a legible response on the other comands, the remount ask for the password then did nothing. This one is formatted ntfs now, been formatted a lot today, fat option doesn't offer 16 or 32 just fat. Only idea I got so far is buy a mac.?

---

### Post by redkilgore on 2014-01-17
I understand that Win files don't support permissions [**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=320715")mc4man, trying to get Unity to stop imposing them, and let me write to my drive. I will stick it back in a win7 machine, reformat fat 32, and properly eject the media to try again.

---

### Post by mc4man on 2014-01-17
> **redkilgore said:**
> I understand that Win files don't support permissions [**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=320715")mc4man, trying to get Unity to stop imposing them, and let me write to my drive. I will stick it back in a win7 machine, reformat fat 32, and properly eject the media to try again.
May be a better test to reformat in ubuntu
Install gparted, open, select drive 
remove current partition, apply, then reformat to FAT, apply

---

### Post by redkilgore on 2014-01-17
The windows format didn't do any good, trying gparted now.

---

### Post by redkilgore on 2014-01-17
Error formatting disk

Error synchronizing after initial wipe: Timed out waiting for objects (udisks-error-quark, 0)

this drive was fine yeserday, I'll try again, then open a new drive thats still in the package, all the others I have here have stuff on them.

---

### Post by redkilgore on 2014-01-17
Here I go again. Brand new 8Gb flash drive, pugged in, popped up, drag file, ERROR while copying - Destination is read only. I'm chasing my tail here.

---

### Post by redkilgore on 2014-01-17
After the new drive didn't work, I went back to the original one, got it to format ext4, it still won't let me write to it, it did let me reset the permissions, set them all to wide open still pops up read only. something is broken. DVD drive won't work either, I've got no way to get my stuff off it to do a clean install. apt-get blue sreen

---

### Post by bab1 on 2014-01-17
> **redkilgore said:**
> After the new drive didn't work, I went back to the original one, got it to format ext4, it still won't let me write to it, it did let me reset the permissions, set them all to wide open still pops up read only. something is broken. DVD drive won't work either, I've got no way to get my stuff off it to do a clean install. apt-get blue sreen

What, no backups?  Shame on you.

Tell is what you modified.  The first thought is the udisks sub-system is not working correctly.

---

### Post by redkilgore on 2014-01-18
No back ups and back online on a windows system, they'll let anybody in here.

I haven't intended to modify anything, I did some cut and paste in term from my initial search for a solution, not sure what I did then but I already had the problem so even if I did damage it was additional not primary. If I can find the live install I used (or make another)  any chance of a repair type situation?

Not a whole lot on it, if I really trim down what I need to keep, a cloud backup may be feasible on flakey AT&T adsl. Bad slow uploads.

If I have to start from scratch, I may try lubuntu or kubuntu, never really liked unity, even though it may not be the problem, it's a good excuse to try something different. Played around with fedora a few years ago, and ubuntu (7.04 maybe), I remember liking the desktops better than Unity, but they just wouldn't play nice with my hardware and do all I needed. Been happy with 13.10 it's done well for me till now, just not in love with the gui.

---

### Post by bab1 on 2014-01-18
> **redkilgore said:**
> No back ups and back online on a windows system, they'll let anybody in here.

I haven't intended to modify anything, I did some cut and paste in term from my initial search for a solution, not sure what I did then but I already had the problem so even if I did damage it was additional not primary. If I can find the live install I used (or make another)  any chance of a repair type situation?


No chmod -R or chown -R?  

You may not like it, but without diagnoses there is no real way to answer the question.  That's what all the "chasing your tail" is about.  Everything is just a guess right now.  I have my doubts about any repair.  It's just easier to just reinstall.  The udisk sub-system is indeed what controls the auto-mounting of USB storage.  I'll bet there is a CLI method to manually mount the flash drive, but .., a keyboard is involved.  ;-)
> 

Not a whole lot on it, if I really trim down what I need to keep, a cloud backup may be feasible on flakey AT&T adsl. Bad slow uploads.

If I have to start from scratch, I may try lubuntu or kubuntu, never really liked unity, even though it may not be the problem, it's a good excuse to try something different. Played around with fedora a few years ago, and ubuntu (7.04 maybe), I remember liking the desktops better than Unity, but they just wouldn't play nice with my hardware and do all I needed. Been happy with 13.10 it's done well for me till now, just not in love with the gui.

Unity is a fork of the new Gnome3 shell.  Ubuntu, Debian and Fedora all use Gnome3.  The old distro that you fondly remember uses Gnome2.  Lubuntu or Kubunu might work and they do not use Gnome at all.  However if you intend on someday setting up file sharing with Windows clients you will be back to Gnome.  No matter which DE you choose they all use Gnome backends to support Samba file shares.

---

### Post by king.of.random on 2014-01-18
What are the permissions of the files you are trying to copy? It maybe that they aren't owned by you. Just a thought, as the permissions of my usb stick are the same as yours and yet I can copy and paste to it.

Also is the trash empty? select "show hidden files" from the drop down menu when you have clicked on your drive and the hidden trash directory will appear check what's in there and delete what you don't need.

---

### Post by squakie on 2014-01-19
could be as simple as specifying ownership and permissions on the mount statement, and then making sure udev isn't stepping on you.

EDIT:  and remember, if you use a mount statement, use the UUID.  Trying to repeatedly use something like "sdg/xxx" isn't reliable as than can chnage on a USB device.

---

### Post by redkilgore on 2014-01-22
Sorry I've ignored my own question for 3 days, working away from home and got the flu, laptop stayed in the suitcase while I crashed on Nyquil. Online in the hotel now.

I would like to resolve this without a re-install just to know what the problem is, and to have it posted for the next guy to find. _But the re-install gets it done._ No big rush right now, so I will keep trying to see what I learn. I got the file I needed moved by booting a live persistent usb and saving it there, I'll back up the rest that way and then it's safe to try most anything since the worst case is to re-install anyway.

I need to do my due diligence and learn some more command line basics so I have the tools to work with. I've forgotten all the DOS commands, and haven't typed a line of BASIC on anything newer than a 80286. Time to dust off the cobwebs and actually take an interest in how a computer works again instead of just treating it like an appliance.

> What are the permissions of the files you are trying to copy? It maybe  that they aren't owned by you. Just a thought, as the permissions of my  usb stick are the same as yours and yet I can copy and paste to it.

All the files I tried were owned by "Me" with R&W access, Group permission is read only. I can access the files within the system fine. ie; Edit, save, delete, etc. a text file I created. It just balks on me on the write process.

Thanks [**[COLOR=#000000]bab1[/COLOR]**]("http://ubuntuforums.org/member.php?u=582150") the Gnome2 vs 3 bit explains a lot and I guess I am stuck with it as Windows files will certainly be a part of my life for the foreseeable future. Always at least 2 windows machines on the home network.

> The udisk sub-system is indeed what controls the auto-mounting of USB  storage.  I'll bet there is a CLI method to manually mount the flash  drive, but .., a keyboard is involved.  :wink:
No promises but I will make an effort, however slow. If an answer shows itself I'll tack it on here.
Thanks again to all of you.

---

### Post by bab1 on 2014-01-23
> **redkilgore said:**
> I need to do my due diligence and learn some more command line basics so I have the tools to work with. I've forgotten all the DOS commands, and haven't typed a line of BASIC on anything newer than a 80286. Time to dust off the cobwebs and actually take an interest in how a computer works again instead of just treating it like an appliance.

Linux is definitely not Windows.  Forget anything you learned about DOS and BASIC.  Those are for Windows OS.  This is Linux.  The default shell is BASH.  It's much more powerful than DOS anyway.   If you need something more powerful there is PERL or Python available as interpreted languages.

If you want to follow the actual execution of a command you can always use strace.  Like this```
strace <command>
```

To check the status of any file or directory you can use stat.  Like this for a file ```
stat <path/to/file>
```

---

### Post by ptn107 on 2014-01-23
I formatted one partition of my thumb drive to ntfs with gparted.  I can read and write to it just fine through nautilus after a quick *chown*.

---

