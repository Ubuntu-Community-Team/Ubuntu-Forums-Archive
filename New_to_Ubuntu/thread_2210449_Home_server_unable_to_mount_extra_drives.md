---
title: "Home server unable to mount extra drives"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by matt70 on 2014-03-10
I have a home server (hp proliant ml350 g5) running ubuntu 13.10 server with 6 drives that are in 3 pairs of raid 1 (hardware raid). 
When I do the "sudo fdisk -l" command I can see the 3 'drives':

Disk /dev/cciss/c0d0 (this is my OS drive that i'd like to keep only the OS on this)
Disk /dev/cciss/c0d1 (single partition FAT32 to be used for users data AKA music, movies, pictures, etc...)
Disk /dev/cciss/c0d2 (single partition FAT32 to be used for users data AKA music, movies, pictures, etc...)

So no issues there I think...

I've worked my way through setting up the OS and getting all the IP addresses correct, I can now get into the two test folders that i placed into a "Files" directory ( matt@server : /files) on both my windows and linux laptops via wifi and rj45.
The two test directories were only placed on the OS drive because that was how one of the examples I was following did it, I would like to have all data on the other two drives (c0d1 and c0d2).

From what I understand I need to mount the other two drives to a location on the OS drive correct? As I understand it I would have two directories in the /files (on the OS drive) one would say something like "Drive A" and the other "Drive B" and when a user opens the "Drive A" directory they would see all the files that are on the /dev/cciss/c0d1 drive and the other "Drive B" would point to /dev/cciss/cd02...

This sounds good but when I run the "sudo mount /dev/cciss/c0d1 public"  ("public" is the name of one of the directories in the /files directory) I get an error message.

Am I doing this wrong? What would the correct way to get this system functioning as I mentioned above? 

Thank you very much for any help!

- matt

---

### Post by steeldriver on 2014-03-10
Hello and welcome to the forums

It would be helpful if you included the actual error message from the mount command - however at a guess you will need to give the full path to the target mountpoint i.e.

```
sudo mount /dev/cciss/c0d1 **/files/**public
```

You *may* also need to add the filesystem type if the system can't autodetect it e.g.

```
sudo mount **-t vfat** /dev/cciss/c0d1 **/files/**public
```

---

### Post by matt70 on 2014-03-11
I pulled the drives and used gparted to make them a single primary partition of the ext4 file system.
When I run the "sudo mount /dev/cciss/c0d1 /files/public" command I get the following: [116.067599] EXT4-f2 (cciss!c0d1): VFS: Can't find valid ext4 file system

Should I try running parted on the server instead? What would the correct command be for formatting these drives so something that ubuntu likes?


thanks!

---

### Post by matt70 on 2014-03-11
*UPDATE* 
After some reading i thought i'd try the ext3 file system instead...

I used: "sudo mkfs -t ext3 /dev/cciss/c0d1" and after it was done i tried " sudo mount /dev/cciss/c0d1 /files/public" and it worked great, i created a directory in the "public" folder and it took with no issues and the correct drive showed activity lights... 
currently changing the file system on the 3rd drive prior to mounting it to the second mount point ( /files/matt in this case)...

Looks like everything has worked out :-)   I never would have thought the file system type would be that big of an issue. 
Is there anything wrong with me using the ext3 file system for my server?  Everything that i have read so far just mentioned the total volume, and file size as limitations but since my two mounded drives are only 500gig each and any files i throw on there will be way less than 10gigs each i can see no issue with what i have done so-far. But am i missing anything?

Also, (this is kinda a self answering question) since i only manually mounted this drive to the /files/public if i reboot the server it will no longer be mounted once the server is back up. I know i can make it automatically mounted, but will there be any indication to the users that they are saving to the OS drive and not the secondary mounted drive? I know that they wont be able to see any info that was on the previously mounted drive if its not currently mounted but will there be an error message? 
The only "easy" fix I can see is to have a secondary directory inside the mount-point-directory AKA: they will only save files to "/files/public/matt" so if they try to save something to a shortcut on their personal directory the shortcut wont work unless the drive is mounted. Obviously this would be a moot point if i just set it up for auto-mounting, I was just wondering if it was best practice to not save files into the mount-point-directory (in my case the /files/public) and always put another directory inside the mount-point-directory? So always do this: /files/public/onlyusethisfile

Thanks!

---

