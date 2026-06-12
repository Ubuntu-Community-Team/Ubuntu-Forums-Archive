---
title: "mount home directory on a different partition"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by cortman on 2011-10-20
Hi friends,

I dual boot my laptop between Windows 7 and Ubuntu 11.10. To make accessing my files easier I created a separate storage partition on my HD using Windows, and formatted it in NTFS. I created the partition in Windows so that Windows would be able to recognize the partition as well as Ubuntu, because I am unaware at least of a way to make Windows access ext formatted partitions.
Therefore, I would like to move my /home folder to this partition, so anything I save in my home in Ubuntu would be on that partition.
How can I do this? Is it even possible?

Thanks!

---

### Post by TeoBigusGeekus on 2011-10-20
It is possible (by altering your fstab file), however I wouldn't recommend it.
Your home partition contains all your user settings (among other things) and exposing it to windows and all its weaknesses (ahem, viruses) is a bit dangerous.
You could use this partition as a storage drive for both windows and ubuntu, but I think you should avoid making it your home partition.
If, however, you insist, we could discuss it.

---

### Post by cortman on 2011-10-20
Would it be possible to make a backup of my user settings just in case? I'm pretty religious about my antivirus software and I'm only rarely on the Web with my laptop, so I think I'd be willing to risk it. If stuff breaks I have no problem re-installing, etc. I've done it many times before.
Or alternately, is there some way to make the partition easier to access from the command line? The only way I access it currently is going to /media/ and typing out the 16 character or so partition name. Any way to re-name, re-mount, etc?
Thanks,

---

### Post by ajgreeny on 2011-10-20
> **TeoBigusGeekus said:**
> It is possible (by altering your fstab file), however I wouldn't recommend it.
Your home partition contains all your user settings (among other things) and exposing it to windows and all its weaknesses (ahem, viruses) is a bit dangerous.
You could use this partition as a storage drive for both windows and ubuntu, but I think you should avoid making it your home partition.
If, however, you insist, we could discuss it.
@TeoBigusGeekus
Are you certain this is even possible?  I have always been under the impression that an NTFS partition will not enable the linux permissions needed for a separate /home partition or folder to work, and that it was therefore impossible to do.

Was that wrong?

I hasten to add that I have no wish, or even possibility, of doing this, not having windows on any of my machines any more, but ask simply to make sure that I am totally correct in my own knowledge base

@OP
I suggest you keep to a separate /data folder and allow all your hidden files and folders used for configuration purposes to sit in the root partition.  Just make sure you keep good updates of those hidden files/folders, which don't take too much room normally.

You can easily mount your windows partition automatically at boot time with the use of **ntfs-config**, installable from the repos, and that way avoid manually mounting it each time you want to use the partition.

---

### Post by cortman on 2011-10-20
Ok, I suppose I don't have to have it in the same partition, it just would have been handy. It can still be handy if I'd have some easier way of getting at the other partition. Is there any better way than accessing it through /media/C28694981206923/my_stuff, etc?
I use the command line a lot, especially for compiling and running some of my homebrew applications, so being able to get at it from the command line easily is important to me.

---

### Post by ArgusVision on 2011-10-20
> Is there any better way than accessing it through /media/C28694981206923/my_stuff, etc?
Yes there definately is. I agree with TeoBigusGeekus that you probably don't want to make this your /home, but if you want it to automatically mount at boot to say /data
you could add it to your fstab.

You can ```
sudo gedit /etc/fstab
```
(Please be careful here. Don't make any changes if you're not certain what it does. )

Add the lines```
# This adds the Windows partition to /data
UUID=[COLOR="Red"]C28694981206923[/COLOR] /data	ntfs	errors=remount-ro	0	0
```
Of course, change the UUID to the UUID of the partition you actually want to mount. 

After you've done this you should be able to access this partition at boot through /data. If you want, you could then symbolically link to the "Folders" in Windows that you want most immediate access to. 
For example:
```
ln -s /data/WINDOWS/Users/cortman/My\ Music Music
```
Would create a short cut in your home folder to your "My Music" folder in the /data partition. 
You can do the same with Documents, Videos, etc.
[COLOR="Red"]One warning though.[/COLOR] If you want to replace the "Music" directory (or other existing directory) in your home directory you'll want to move the files and delete the directory. Then create the link and move the files into the new 'linked' directory.

I do a similar thing with multiple Linux OS'es on my machine.

---

### Post by collisionystm on 2011-10-20
> **cortman said:**
> Hi friends,

I dual boot my laptop between Windows 7 and Ubuntu 11.10. To make accessing my files easier I created a separate storage partition on my HD using Windows, and formatted it in NTFS. I created the partition in Windows so that Windows would be able to recognize the partition as well as Ubuntu, because I am unaware at least of a way to make Windows access ext formatted partitions.
Therefore, I would like to move my /home folder to this partition, so anything I save in my home in Ubuntu would be on that partition.
How can I do this? Is it even possible?

Thanks!


Easy. You just need to know the absolute path to your new home folder. You do not need to edit /etc/fstab.

First, 

Ubuntu should be automatically recognizing your ntfs partition on startup. If not, just use ntfs-config from the software center to make this happen.

Second,

Open terminal

If you know the path to your new home folder, just edit the /etc/passwd file to point yourself there.

sudo nano /etc/passwd

scroll down to your username, should be at the bottom.

change the part of the line that says /home to /PathToNewHome

CTRL + X then Y to save.

Log out and back in.

Your profile will be at default. DO NOT PANIC.

Just go to your hold home folder, copy your files in there and paste them into the new one. Ubuntu should have automatically created the new folders for you on the ntfs volume so everything will just line up.

---

### Post by cortman on 2011-10-20
@ArgusVision- This makes sense! I'll try that, it looks like it ought to be just what I want. Thanks a lot!

---

### Post by collisionystm on 2011-10-20
And yeah, Linux CANNOT write permissions to an NTFS partition. This may cause you some trouble along the way. None the less. Good Luck.

---

### Post by gsmanners on 2011-10-20
For removable NTFS drives, I would suggest using ntfslabel. Just putting that out there (in case someone is searching for this info later).

---

### Post by ArgusVision on 2011-10-20
@cortman You're welcome.
Also I'm pretty sure collisionystm is right so you probably only want to use this with standard filetypes. (.doc,.mp3,.jpg,etc.)
As opposed to critical configuration files.

---

### Post by cortman on 2011-10-24
> **collisionystm said:**
> And yeah, Linux CANNOT write permissions to an NTFS partition. This may cause you some trouble along the way. None the less. Good Luck.

So there's no way to change permissions on a file if it is on an NTFS partition? Chmod wasn't working by default but I wasn't sure if I just wasn't doing something right.

---

### Post by TeoBigusGeekus on 2011-10-24
> **ajgreeny said:**
> @TeoBigusGeekus
Are you certain this is even possible?  I have always been under the impression that an NTFS partition will not enable the linux permissions needed for a separate /home partition or folder to work, and that it was therefore impossible to do.

Was that wrong?

I hasten to add that I have no wish, or even possibility, of doing this, not having windows on any of my machines any more, but ask simply to make sure that I am totally correct in my own knowledge base


Ha!!! Touche mate, you're absolutely correct, I didn't think of that.
I've never tried it anyway, nor do I intend to...

---

### Post by oldfred on 2011-10-24
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I use the same mount & link as ArgusVision for both a NTFS partition for Firefox & Thunderbird profiles & some common data with my XP install and a ext3 partition for Linux only data. I like to mount in /mnt/shared & /mnt/data so they are only visible when going to computer & drilling down. Links provide all the access in /home I need.

For the profiles I just edit profile.ini in both Thunderbird & Firefox to look to the NTFS partition from both Windows & Linux. 

Pretty much the same as ArgusVision posted above.
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

---

### Post by Gadgetech on 2011-10-24
To access ext2/3/4 partitions from Windows, I've used ext2fsd in the past. It's worked well for me. You can configure it to auto mount when you start Windows or you can manually mount from the system tray. It's even free software, licensed under GPLv2.

For me this is much better than trying to put /home on an NTFS partition.

[http://sourceforge.net/projects/ext2fsd/]("http://sourceforge.net/projects/ext2fsd/")
[http://www.ext2fsd.com/?page_id=2]("http://www.ext2fsd.com/?page_id=2")

---

