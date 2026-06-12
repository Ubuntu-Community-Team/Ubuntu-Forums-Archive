---
title: "Can't acess my fstab mounted ext3"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Thorun on 2008-04-29
I have formatted a partition with ext3 and wanted to mount it in fstab. 
My fstab file looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> 				<mount point>   	<type>  	<options>       		<dump>  <pass>

proc            				/proc           	proc    	defaults        		0       0

# /dev/sda9
UUID=84239e72-65d8-4020-9ae5-7a9872e028fd 	/               	ext3    	relatime,errors=remount-ro 	0       1

# /dev/sda5
UUID=9bf95716-5b66-49ea-a368-8c562a4ae8c8 	none            	swap    	sw              		0       0

# Linux partition 2
# /dev/sda6
#defaults,errors=remount-ro
UUID=83a844ba-5a4d-4b08-b422-982b4cf344d2 	/media/linuxpart 	ext3 		defaults			0	1

# Linxa-stuff
# /dev/sda7 :
UUID=0E706B71706B5F09 				/media/linxa-stuff 	ntfs-3g 	defaults,locale=da_DK.UTF-8 	0 	1

/dev/scd0      	 				/media/cdrom0   	udf,iso9660 	user,noauto,exec,utf8 		0       0
```

The ext3-partition is allright mounted and there is a shortcut on my desktop to the files. The problem is: I have no rights to acess anything on the partition. It is wery much locked. I can't even make a new folder/file. 

What do i have to do, with the sda6 in fstab? 
I use 8.04.



Edit:
I can't even access anything on the partition when i mount it via the "places -->  disk". Hmm. I think that fstab isn't the problem at all. Maybe it's some right that i don't have .. or something...

---

### Post by plucky on 2008-04-29
See this [link](http://www.psychocats.net/ubuntu/mountlinux) for the psychocats website and some very useful information.


Good Luck.

---

### Post by stchman on 2008-04-29
> **Thorun said:**
> I have formatted a partition with ext3 and wanted to mount it in fstab. 
My fstab file looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> 				<mount point>   	<type>  	<options>       		<dump>  <pass>

proc            				/proc           	proc    	defaults        		0       0

# /dev/sda9
UUID=84239e72-65d8-4020-9ae5-7a9872e028fd 	/               	ext3    	relatime,errors=remount-ro 	0       1

# /dev/sda5
UUID=9bf95716-5b66-49ea-a368-8c562a4ae8c8 	none            	swap    	sw              		0       0

# Linux partition 2
# /dev/sda6
#defaults,errors=remount-ro
UUID=83a844ba-5a4d-4b08-b422-982b4cf344d2 	/media/linuxpart 	ext3 		defaults			0	1

# Linxa-stuff
# /dev/sda7 :
UUID=0E706B71706B5F09 				/media/linxa-stuff 	ntfs-3g 	defaults,locale=da_DK.UTF-8 	0 	1

/dev/scd0      	 				/media/cdrom0   	udf,iso9660 	user,noauto,exec,utf8 		0       0
```

The ext3-partition is allright mounted and there is a shortcut on my desktop to the files. The problem is: I have no rights to acess anything on the partition. It is wery much locked. I can't even make a new folder/file. 

What do i have to do, with the sda6 in fstab? 
I use 8.04.



Edit:
I can't even access anything on the partition when i mount it via the "places -->  disk". Hmm. I think that fstab isn't the problem at all. Maybe it's some right that i don't have .. or something...

Change the ext3 line to this:
```

# Linux partition 2
# /dev/sda6
#defaults,errors=remount-ro
UUID=83a844ba-5a4d-4b08-b422-982b4cf344d2 	/media/linuxpart 	ext3 		auto,defaults,rw			0	0
```

Then do the following:

Change ownership of the drive to the user that needs it.
```
sudo chown -R $USER:$USER /media/linuxpart
```

Allow the user to read and write to the drive.
```
sudo chmod -R 755 /media/linuxpart
```

That should do it.

I have a more thorough tutorial on partition mounting.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by Thorun on 2008-04-29
Thank you both for good answers. I changed the fstab and set the ownership of the disk - and now it works wery well. 

Do any of you by chance know, why the fstab in 8.04 isn't auto-mounting every single partition like the 7.10 did?
I know that there's a new (i think) feature where you just can mount the drive from "places", but i don't know if 8.04 just switched the one feature for another. 


And - how does i make this thread "solved" ? Can't find any button.

---

### Post by stchman on 2008-04-29
> **Thorun said:**
> Thank you both for good answers. I changed the fstab and set the ownership of the disk - and now it works wery well. 

Do any of you by chance know, why the fstab in 8.04 isn't auto-mounting every single partition like the 7.10 did?
I know that there's a new (i think) feature where you just can mount the drive from "places", but i don't know if 8.04 just switched the one feature for another. 


And - how does i make this thread "solved" ? Can't find any button.

The fstab does not auto-mount filesystems.  Nautilus will show them.

The fstab method is the best and most secure way to mount file systems.

---

