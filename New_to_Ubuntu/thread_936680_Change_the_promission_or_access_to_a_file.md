---
title: "Change the promission or access to a file"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by articwolf939 on 2008-10-03
i have an external HD hooked up to my cpu but i is only read access and i want to be able to save things in it so i need to change it to, read and write how do i do that and idea?

im using festy fawn

---

### Post by articwolf939 on 2008-10-03
Ooo commmon no one know how to do this >.<

---

### Post by NovaAesa on 2008-10-03
I know that it could be done using the command line application "chown" but unfortutately I don't know how to use it. Maybe someone else will come along that knows how to use "chown" or another way of doing it.

---

### Post by perlluver on 2008-10-03
That command is sudo chown username /media/drive or wherever it is set to.

---

### Post by articwolf939 on 2008-10-03
it said

chown: ownership of '/media/disk-1': read-only file system

how can i change it read and write

---

### Post by nothingspecial on 2008-10-03
Is the drive ntfs? Because if so I don`t think Ubuntu provided ntfs read and write support until Gutsy.

---

### Post by articwolf939 on 2008-10-03
yea i formatted it in windows, can i reformat it somehow for linux and will the ps3 still read it? or would it be easiest to just install gusty

---

### Post by nothingspecial on 2008-10-03
Here`s some reading

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by ZhuaSD on 2008-10-03
If you formatted in Windows than it is Fat or ntfs, fat you can read and write to in Linux, NTFS you can only read, I think...

I had some partitions that were unmountable because they were ntfs, so I converted them.

you can convert ntfs to fat, I did it in Windows cuz I am lazy, I took off almost all the data to be careful but it looks like the data will be ok. I used Partition Magic for that.  Then I could mount and read and write

---

### Post by hyper_ch on 2008-10-03
you can format the drive to ext3 and install the ext2/3 drivers on windows OR you will use ntfs-3g to be able to read/write to the ntfs drive in linux. I'd not use Fat32 anymore.

---

### Post by pmooney78 on 2008-10-03
I went through the same thing migrating from Windows to Xubuntu. Here's a few things to check, in increasing order of complexity:

1. If the drive is ntfs, Xubuntu *CAN* read it, but you need to install the ntfs-3g package. Try typing "sudo apt-get install ntfs-3g" in a terminal. 

2. In your application menu, choose "System," then "users and groups." Click on "unlock," then type your password. Click your user name, then "Properties." On the "User privileges" tab, make sure you have "Access external storage devices automatically" checked. 

3. If neither of those is the problem, you might need to modify your /etc/fstab file. This is a file that sets out general permissions for drives attached to the system -- where they mount in the file system hierarchy, what privileges each logical drive has, etc. There's a good general tutorial here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Essentially, you want to make sure that the drive is auto-mounted, and that it has the "users" tag. You need to figure out your drive's physical location first -- if it's an external USB drive, it's probably something like /dev/sd[some letter][some number]. You can use the partition editor to figure it out, sometimes. Type "gparted" in a terminal. If it complains, type "sudo apt-get install gparted", and try typing "gparted" again when that finishes. It'll scan your drives. I can always identify my drives by size, but you might need to examine more closely.

Once you know that, type "gksudo mousepad /etc/fstab", type your password, and find the entry in the fstab file that corresponds to /dev/sd[some letter][some number] that you figured out using gparted. Look at the line, which should look something like this (borrowed from my own fstab file):

(By the way, it's always a good idea to make a backup of your fstab file before editing. I just save it to /etc/fstab.bak, then open up the original /etc/fstab file again [because I want to modify the original and not the backup].)

/dev/sde1 /media/Externa ntfs-3g async,user,utf8,gid=100,auto 0 1

You can ignore the two numbers at the end. A couple of things to check here: First, the drive type should be "ntfs-3g" if it's an ntfs drive, or "vfat" if it's a FAT drive. (NTFS is a better choice if you have to share data with a Windoze system!) There are lots of options for the third column, but make sure you have at least "user" (which means, everyone can mount it) and "auto" (which means, it auto-mounts as soon as it's connected, or when you start up) chosen. Save your changes.

4. Still not working? The discussion about permissions early was semi-right. You can't directly change ownership of files and folders on a Windoze-format drive (because NTFS and FAT don't really support Unix-style ownership of individual items), but there's an alternative: Linux treats all files on a foreign[LEFT][/LEFT] drive as if they were owned by the same user and group. That's what the gid=100 item is about in the fstab excerpt above. 100 is the group ID for the "users" group on my system, but it might be different on yours. (I don't think it's likely, but it's possible. Check to be sure.) You can figure it out by dinking around with the Users and Groups application mentioned above, or you can examine the /etc/group file to figure out the group ID. (Type "man group" in a terminal for information.) Add ",gid=[whatever]", without the brackets, to the appropriate line in your /etc/fstab file. 

5. One more option, and again, the discussion about ownership was semi-right. You can't change ownership of individual files and folders on the foreign drive, but ... the drive is actually mounted at a specific point on your main ("root") file system. This point is a folder. Under the right circumstances, you can change the ownership of that folder. Open a terminal and unmount the drive. You can do this by right-clicking the drive's icon on the desktop or in Thunar and choosing "Eject", or type "umount Externa" (or whatever your drive's name is) in a terminal. Try putting a "sudo" in front of that if it doesn't work. 

Then, once the drive is unmounted, type "sudo chown patrick:users /media/Externa" (substitute your username for "patrick" and your drive name for /media/Externa").

Hope that helps...

---

### Post by SoggyCornflake on 2008-10-05
> **NovaAesa said:**
> I know that it could be done using the command line application "chown" but unfortutately I don't know how to use it. Maybe someone else will come along that knows how to use "chown" or another way of doing it.

The way I've most often used it is like 
```
chown username:groupname /filelocation/file

```

for example, as  super user I copied a file to my kid's directory and then changed the ownership to his username and group
```
sudo cp /home/SoggyCornflake/coolvid.avi /home/timothy/coolvid.avi
sudo chown timothy:timothy /home/timothy/coolvid.avi

```

---

### Post by hyper_ch on 2008-10-06
> **pmooney78 said:**
> 1. If the drive is ntfs, Xubuntu *CAN* read it, but you need to install the ntfs-3g package. Try typing "sudo apt-get install ntfs-3g" in a terminal. 
Wrong. ntfs-3g is only required for WRITING to a ntfs drive.

---

### Post by didiercool on 2008-10-06
> **articwolf939 said:**
> it said

chown: ownership of '/media/disk-1': read-only file system

how can i change it read and write

If the only problem is the permission, then use chmod (change mode) to manipulate permissions.  You might need to use super-user-do (sudo) for this, I don't remember.  To check the permission of a file or folder type > ls -l /media/disk-1.  r's for read, w's for write, x's for execute.  To change the permission of a file or folder use > sudo chmod 755 /media/disk-1  A read permission is 1, a write permission is 2, and an execute permission is 4.  Adding these in various combinations will give you all the options you need.  7 = 1+2+4, read, write and execute, 5 = 1+4, read and execute, etc.  The first number pertains to the owner of the file, the second and third numbers pertain to other users and processes (I think).  So 755 will give you read, write, and execute privileges and all else read and execute privileges.

Hope this helps!

---

