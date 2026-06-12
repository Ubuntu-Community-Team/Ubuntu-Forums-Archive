---
title: "Is this chmod command line correct?"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Greenwick on 2011-10-06
I have an MP3 player which has suddenly been made read only for reasons I haven't figured out yet.  After looking online, I found out about chmod as a way to change permissions.  I've never heard of chmod before, and would like to make sure that I'm using the right thing before I go and screw my system up.  (I am going off of what I read in the [chmod Wikipedia article]("http://ubuntuforums.org/en.wikipedia.org/wiki/Chmod").)

So according to the article, I would type this command line to ensure all users can read and write to the device.

> $ chmod 777 *file*
Two questions:

-Is there anything else I need to add to that?  I don't know how to specify that I want the permissions on the MP3 player to be changed.  I'm assuming if I just typed this command in, that it wouldn't work for the MP3 player.

-Is this even appropriate for a device?  I am assuming 'file' is meant to be replaced by the file name, but in this case it is the whole device that needs changing.  

Thanks so much!

---

### Post by WasMeHere on 2011-10-06
Hello Greenwick!

```
chmod 777 file
``` means that you set
**r**ead **w**rite e**x**ecute for **u**ser **g**roup **o**thers
This is equiavalent to 
```
chmod ugo+rwx file
```
and gives everybody access to do everything to your file. Maybe you would not like others to write or remove your file. In that case run
```
chmod o-w file
```
Check the result with
```
ls -l file
```

In order to modify all files in a directory and its subdirectories run
```
chmod -R 777 directory
``` and your files will be readable and executable for everybody. If there are problems with the access, run as root (superuser)```
sudo chmod -R 777 directory
```
Do not operate on a drive!
- Mount the drive (to a directory)
- Open a terminal window and change directory, *cd*, to the directory where the drive is mounted.
- Run the chmod command

Good luck
Olle

*Edit: mcduck, I answered the question, but you solved the problem.*

---

### Post by mcduck on 2011-10-06
In addition to above, it should be noted that since it's an MP3 player, the file system it uses is most likely FAT. Which doesn't support Posix permissions, so chmod command will have absolutely no effect on any file or directory located on the device.

Permissions for file systems that lack support for Posix permissions (FAT and NTFS, most commonly) are instead set for the whole filesystem, at the time it's mounted.

Anyway, if the player was normally writeable before, which should be the default behavior for any FAT filesystem, the reason for it suddenly becoming read-only would most likely be that there has been some error when trying to write to the device, and the Linux kernel changed it to read-only mode to protect it from any further damage. If that's the case, the actual permissions have nothing to do with the situation, and the only way to recover from it would be to repair the filesystem or format the device.

---

### Post by audiomick on 2011-10-06
+1 mcduck

---

### Post by Greenwick on 2011-10-06
Thanks!  I did try the commands you gave me, Olle, just in case, but Mcducks's suggestion was right.  Thanks, though!  (I am sure that learning about chmod files will come in handy in the future, so I'm glad that I came across those anyway.)

I tried to reformat using the disk utility, which did say the MP3 is FAT 32.  I reformatted it, and then created a new partition.  Now it works!  Awesome!

Thank you so much!

---

### Post by WasMeHere on 2011-10-06
You are welcome :-)
Please mark the thread SOLVED!

---

### Post by Greenwick on 2011-10-06
Just a quick note for anyone finding this thread on the internet: When I clicked play nothing happened.  I had reformatted the MP3 player as something other than FAT.  I was about to make another topic to figure out what to do when I realised this was probably the cause.  So I reformatted the MP3 player as a FAT system and now it works.

---

