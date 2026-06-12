---
title: "Changing Non-boot HDD permissions."
date: 2016-04-10
forum: New to Ubuntu
---

### Post by 00b00nt00 on 2016-04-10
Situation:

I have two disk drives inside my system: a 250GB SSD OS boot drive, and a 2TB HDD which I would like to use for storage.

Now, I have full read/write access to the boot drive, but when I format the HDD as ext4, I can't access it! Permissions list the owner as 'root', and that's not me. How can I change the permissions so that I can have read/write access on the drive, short of formatting it FAT32?

Thanks in advance.

---

### Post by Dennis N on 2016-04-10
> **00b00nt00 said:**
> ...Now, I have full read/write access to the boot drive, but when I format the HDD as ext4, I can't access it! Permissions list the owner as 'root', and that's not me. How can I change the permissions so that I can have read/write access on the drive, short of formatting it FAT32?

Thanks in advance.

Suppose that you are mounting the ext4 partition you created on the 2nd drive at /mnt/data.
All you need to do is change the owner and group of that mount folder to your user name:

If your user name is mary:

[FONT=Courier New]**sudo chown -R mary:mary /mnt/data**[/FONT]

Since you would now be owner, you get all the permissions given the owner, including read and write.

---

### Post by 00b00nt00 on 2016-04-10
Worked like a charm and took all of 30 seconds. You're a star.

For reference, I found the mount point by typing *mount* in the terminal and searching for the volume, which I knew to be sdb1.

---

### Post by Dennis N on 2016-04-10
Thanks for the feedback. Owned file systems on newly created partitions always initially belong to root, so this will happen again should you make more partitions.

---

### Post by ajgreeny on 2016-04-10
You should probably be mounting this partition with the /etc/fstab file, if you're not already doing so, to avoid having to click on the disk icon in your file-manager or on the desktop.

If you need to know more about this come back again and ask.  Having mounted it that way you can also create symbolic links from the various folders in that second disk's partitions to your /home folder, which I assume is on the SSD, so that it will appear as though the data files are sitting in your home.

---

### Post by 00b00nt00 on 2016-04-11
> You should probably be mounting this partition with the /etc/fstab file, if you're not already doing so, to avoid having to click on the disk icon in your file-manager or on the desktop.

Interesting. If you have time for a quick tutorial, I'll give it a shot.

---

### Post by oldfred on 2016-04-11
I prefer to mount at /mnt/data so mount is not shown in Naulitus. And then link folders into /home, so I do not ever drill down from /, to /mnt to /mnt/data and then to my data.
But you can mount in /media or /media/$USER which is a default for external drives/partitions.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab
[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

I have multiple installs, so I mount data partition in each. But even with one install you can separate /home from /mnt/data.

 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata) 

[URL="https://help.ubuntu.com/community/Fstab"]
[/URL]

---

### Post by frogotronic on 2016-04-11
> **oldfred said:**
> I prefer to mount at /mnt/data so mount is not shown in Naulitus. And then link folders into /home, so I do not ever drill down from /, to /mnt to /mnt/data and then to my data.
But you can mount in /media or /media/$USER which is a default for external drives/partitions.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab
[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

I have multiple installs, so I mount data partition in each. But even with one install you can separate /home from /mnt/data.

 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata) 

[URL="https://help.ubuntu.com/community/Fstab"]
[/URL]

I also have this problem, but with a wrinkle.  I would like to have the second HDD mounted at boot, but there are multiple user logins.  Is there a way to have it mounted for everyone (regardless) of who logins to the machine?

---

### Post by oldfred on 2016-04-11
@cement-head
Better to start your own thread.
You are into ownership & permission group issues, otherwise similar. But you may not want to mount in one user but in /mnt or /home but not /home/$USER.
And whether all can edit and delete, or only read or write.
But I do not know permissions that well other than just for me.
Some Links.
       Group Permissions - Morbius1
[URL="http://ubuntuforums.org/showthread.php?t=2138476"]http://ubuntuforums.org/showthread.php?t=2138476
[/URL]
 Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)
[http://askubuntu.com/questions/642648/use-common-data-folders-for-two-users-instead-of-separate-ones](http://askubuntu.com/questions/642648/use-common-data-folders-for-two-users-instead-of-separate-ones) 

[URL="http://ubuntuforums.org/showthread.php?t=2138476"]
[/URL]

---

### Post by frogotronic on 2016-04-11
okay, thanks - I'll start a new thread

---

