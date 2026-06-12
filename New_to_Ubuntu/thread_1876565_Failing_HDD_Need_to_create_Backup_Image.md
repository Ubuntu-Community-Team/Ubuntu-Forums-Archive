---
title: "Failing HDD Need to create Backup Image"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by JoeNaz2003 on 2011-11-06
First let me begin by saying this is my first time running any kind of Linux software. Sorry this is so long but I want to be as thorough as possible. Also sorry if it was covered elsewhere. I looked but I was searching so frequently and frantically the forum search was glitching out on me.

I have a 1TB WD HDD removed from a 1TB Buffalo NAS station with about 500GB of un backed up Pics,Data and Music. Of course my home videos, Photos and Data are more important to me than the music or movies on the drive. It is an XFS file system. The NAS was split into about 7 main folders which allowed different users to access each one.
 
I received an error and the disk could not be read after 2 power outage in a row.

I have tried copying the disk with Windows UFS Explorer to no avail. It stops at 6.3% and the estimated time just keeps increasing. I stopped it when it hit an estimate of about 200 hours to complete as I don't want to run it any longer and risk damaging the drive further.

After installing it in Ubuntu the disk utility SMART scan is telling me I have:

Bad Sectors: 1265
Overall Assessment: Disk Failure Is Imminent Backup all data and replace disk
Attribute 5. Reallocated Sector Count (FAILING)
Normalized: 41
Worst: 41
Threshold: 140
Value: 1265 sectors


I would like to make an image of the HDD.

What I have is Ubuntu 11.10-desktop-amd64 installed on its own 1TB drive (/dev/sda1)
I would like to make a copy of the damaged disk 1TB (/dev/sdb1)

I have installed GNU ddrescue but being a windows user I have no idea what to do.

Can anyone please help?

Please excuse my Super Noobness.

---

### Post by Rex Bouwense on 2011-11-06
I believe that clonezilla is what you need.  See here:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by BillyBoa on 2011-11-06
Sometimes backup is the trigger to death of the HDD. Maybe is better to try copying the files instead of a executing a full backup.

---

### Post by dannyboy79 on 2011-11-06
you say it's an XFS system but what I am not clear on is how many partitions it contains, also you mentioned it being a 1TB HDD, is that correct?

I believe ddrescue requires the exact same amount of storage on the new drive as the old drive. Meaning if it's 1TB but you're only trying to save 500gb of data, you still need to be saving onto a 1TB drive.

i would strong suggest IF you're ddrescueing TO the /dev/sda FROM /dev/sdb that you use a live cd or live USB install (versus being in an installed OS which is the same drive you're backing up to). 

Here's an example of a guy saving an image file of only 1 partition: [http://vmwaretips.com/wp/2009/01/29/my-hdd-failed-but-ddrescue-saved-the-day/](http://vmwaretips.com/wp/2009/01/29/my-hdd-failed-but-ddrescue-saved-the-day/)

---

### Post by JoeNaz2003 on 2011-11-06
I tried to copy the files first but nothing seems to read the disk.

Yes its a 1TB drive. I was hoping since I could start an image and stop then restart where it left off I would be able to extract the data portions needed and save them then continue. Like I said I'm a super noob. I've never lost a HDD and I've been using and building computers since I got my first Comadore 64. Ill read up on the links you guys have given me.

Also my partitions on the drive are:
1.0GB ext3 (sdb1)
5.1GB xfs (sdb2)
0.5GB unknown (sdb3)
0.5GB unknown (sdb4)
1.0GB swap space (sdb5)
985GB Filesystem (sdb6)

All partition types are Linux Basic Data Partions. I didn't notice the sdb1-6 until just now.

---

### Post by JoeNaz2003 on 2011-11-06
OK here is my update. I went out today and purchased another 1TB drive. Now can anybody set me in the right direction? Keep in mind this is my first time using any kind of Linux software and the last thing I did in something that looked like a terminal window was goto loop commands lol.

---

### Post by pierreyy on 2011-11-06
since your using 11.10 do you have an application that is called " backup"  the icon is a safe.... i checked it out, its very easy to use... i guess just plug in your hdd and enter the correct inforation in the application, then click on "BACKUP NOW" i think that should be it... if im not mistaken,,, good luck!

---

### Post by JoeNaz2003 on 2011-11-06
Yes I do have that. And you know I've been buying and downloading software for days not even thinking to try it since the hard drive is failing I just assumed I needed something recovery wise.

---

### Post by wildmanne39 on 2011-11-06
Hi, Rex Bouwense gave you one of the best options but if you can not copy files then it is probably to far gone.

Two weeks ago I knew I had a disk going bad but it was still booting so I tried clonzilla it failed at cloning the grub because it caused the hard drive to go ahead and die, but it cloned all the other files, then I just installed 11.10 and did not format the home partition and I had all my files and settings when the install finished, but you have to have a separate partition for home to be able to do it this way and you have to be able to at least clone your home partition.

At the link you can download clonzilla read how to make it boot then follow on screen directions.
Thank you

---

### Post by JoeNaz2003 on 2011-11-06
As i said above I can see the disk and the SMART scan shows 1256 bad sectors and from what I was reading 500GB has about 900,000,000 sectors I have a 1TB but only 500GB used so I'm hoping I didn't lose too much data. The issue I'm having is the NAS was on a Win7 system but uses XFS file system which is read by Linux so I have only been using Linux for about 16 hours. I purchased UFS explorere which is what people in other forums who have had the same NAS drive crash used but it keeps locking up at about 6.3%.

---

### Post by pierreyy on 2011-11-06
> **JoeNaz2003 said:**
> Yes I do have that. And you know I've been buying and downloading software for days not even thinking to try it since the hard drive is failing I just assumed I needed something recovery wise.


great ...now its either that or clonezilla and honestly if i could help i would but i dont have much experiencxe with hdd deaths:P good luck!!

---

### Post by dFlyer on 2011-11-06
I don't think backup from 11.10 will do it for you. I had a drive going bad and tried that and it did backup everything in my home folder to my external drive. I figured great, but on restore it would crash about half way into the restore with corrupt files. Luckly I didn't wipe the drive and ended up backing up by copying folder to a backup external drive. It took a while to backup everything that way, but at least I have all my data files on a backup drive that are restore-able. I did end up having to skip a few files that were damaged and wouldn't backup, but that was a very small number compared to what I saved.

---

### Post by JoeNaz2003 on 2011-11-06
I tried to get into it but after the power outage/strike I had, the Buffalo NAS drive would no longer boot and the way its partitioned and being XFS I can't even read it to get to the folders. If I could it would be great. That would make my life a lot easier. I would get whats salvageable off, delete those files and then try to restore the rest.

The screwed up part of this is I just finished backing up actually moving 100's of movies and TV shows I had on the drive and another drive to condense them. Why I didn't get my pics and data off first is beyond me.

---

### Post by dannyboy79 on 2011-11-07
ok, i would suggest creating some ext3 partitions on your new 1TB drive. make them around 50GB larger then the partitions you are trying to create images of using ddrescue. then just follow the link i posted earlier.
[http://vmwaretips.com/wp/2009/01/29/my-hdd-failed-but-ddrescue-saved-the-day/](http://vmwaretips.com/wp/2009/01/29/my-hdd-failed-but-ddrescue-saved-the-day/)

---

### Post by JoeNaz2003 on 2011-11-07
OK so I should partition the new drive before creating a backup image file?

---

### Post by dannyboy79 on 2011-11-07
> **JoeNaz2003 said:**
> OK so I should partition the new drive before creating a backup image file?
well, that's my suggestion yes.

---

### Post by JoeNaz2003 on 2011-11-07
OK I'm gonna give it a try in about an hour. I'll let you know how it turns out.

---

### Post by dannyboy79 on 2011-11-07
me personally, I carry around a 16GB Verbatem USB Stick which I have several OS's on which I put on it using Multisystem Boot. It installs grub2 on the MBR of the stick, I have 11.10 with persistance, 10.04 (non-persistance) I have SystemRescue CD, and Clonezilla and they all can be booted if I tell the BIOS to boot to my 16GB usb stick. It's awesome!!

Here's a good tutorial but instead of imaging the entire HDD, you would be imaging single partitions at a time. Just a suggestion.

---

### Post by JoeNaz2003 on 2011-11-07
Other than multi boot of the USB stick I have no idea what you said which is why I'm having issues.

What I have so far is:
The original drive I want to image is sdb
The new drive is sdc

From what I can tell the main data partition which I believe from all the reading is what I want to image first.

This is the command string that I came up with. Does it seem right or am I missing something? I have not partitioned the 2nd drive, from what I was reading I don't think I have to but I'm still not sure on that.

ddrescue -r3 /dev/sdb6 dev/sdc/sdb6.image /sdb6.logfile 
 
or if I partition the new drive which from what you said I should, it would be

ddrescue -r3 /dev/sdb6 dev/sdc6/sdb6.image /sdb6.logfile

---

### Post by dannyboy79 on 2011-11-07
> **JoeNaz2003 said:**
> Other than multi boot of the USB stick I have no idea what you said which is why I'm having issues.

What I have so far is:
The original drive I want to image is sdb
The new drive is sdc

From what I can tell the main data partition which I believe from all the reading is what I want to image first.

This is the command string that I came up with. Does it seem right or am I missing something? I have not partitioned the 2nd drive, from what I was reading I don't think I have to but I'm still not sure on that.

ddrescue -r3 /dev/sdb6 dev/sdc/sdb6.image /sdb6.logfile 
 
or if I partition the new drive which from what you said I should, it would be

ddrescue -r3 /dev/sdb6 dev/sdc6/sdb6.image /sdb6.logfile
First question, will you be booting into a LIVE CD or LIVE USB System? I would strongly suggest it as I mentioned earlier. The thing I don't think you're understanding is that you HAVE to partition and format you NEW drive because all you're doing is saving an image file. You're not cloning partitions or hard drives, you're using ddrescue to spit out byte by byte into an image file.

So, if for example your bad hdd partition sdb6 per fdisk -l is 100gb in size, then if I were you I would create your first partition on your new hdd sdc1 and make it 110gb (10gb larger then bad partition) in size and format is using the ext3 FS type.

if you did that above, this is what you would do within your live linux OS

```
mkdir /mnt/sdc1
```
```
mount /dev/sdc1 /mnt/sdc1
```
```
ddrescue -r3 /dev/sdb6 /mnt/sdc1/sdb6.image /mnt/sdc1/sdb6.logfile
```

I you read the whole article I keep linking to I think you'll better understand what you're doing and why. [http://vmwaretips.com/wp/2009/01/29/my-hdd-failed-but-ddrescue-saved-the-day/](http://vmwaretips.com/wp/2009/01/29/my-hdd-failed-but-ddrescue-saved-the-day/)

---

### Post by JoeNaz2003 on 2011-11-07
I have Ubuntu installed on its own drive. I figured that would be better than the Live CD option.

I was trying to format the partitions using gparted but for some reason I cant seem to fit as many partitions at the size they are. The drive I'm trying to image is also coming up as unknown file system for 2 of the partitions in disk utility but they are only .5kb each.

I've read that and the online manual for gddrescue many many times and each time I read it my brain begins to hurt more and more lol. I'm sorry again for my problems but I am about as new at this as it gets.

I'm going to upload some pics of what disk utility is telling me.
I have 6 so there will be 1 straggler which is where I think my saved data is stored.

---

### Post by JoeNaz2003 on 2011-11-07
This is the 6th partition

---

### Post by JoeNaz2003 on 2011-11-07
Before I even partition the new 1TB drive its comming up as 931.51GB unallocated. But just partition 6 on the drive i'm trying to image is 985GB

---

### Post by dannyboy79 on 2011-11-07
> **JoeNaz2003 said:**
> Before I even partition the new 1TB drive its comming up as 931.51GB unallocated. But just partition 6 on the drive i'm trying to image is 985GB
HUH, that is weird. I forgot about FS overhead. So you're positive that your new 1TB drive is completely blanked out, erased, no partition table or nothing!

How did you partition this /dev/sdb drive before, when it was in your Buffalo NAS?

---

### Post by JoeNaz2003 on 2011-11-07
My new empty drive shows as 1TB free when I view in disk utility. 

But when I bring it up in GParted it shows:
Partition - unallocated
File System - unallocated
Size - 931.51GB unallocated

I didn't partition the NAS drive it was a Buffalo 1TB NAS. It came ready to go. All I did was add a folder for each user/directory then set permissions up through the NAS control panel which was web based like a router and accessed through the NAS IP adress.

I have more pics. Sorry I just got shutter, this thing is awesome.

---

### Post by dannyboy79 on 2011-11-07
show me what gparted looks like when you show the /dev/sdb drive.

---

### Post by JoeNaz2003 on 2011-11-07
This is sdb

---

### Post by dannyboy79 on 2011-11-07
ok, so make a 920 gb partition on your new HDD. then just follow my directions I already posted.

---

### Post by JoeNaz2003 on 2011-11-07
920gb xfs partition since thats what the file system on the bad drive is correct?

---

### Post by gamblor01 on 2011-11-07
Looks like this has pretty much already been answered but I thought I would throw in my 2 cents.  If you need to get down and dirty with the command line to copy then this post from Saikee over at justlinux.com is an excellent resource.  Specifically, read the steps in blue:


[http://www.justlinux.com/forum/showthread.php?threadid=149328](http://www.justlinux.com/forum/showthread.php?threadid=149328)




And if you need to recover data from a hard drive, here is an EXCELLENT guide for how to do that:


[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by JoeNaz2003 on 2011-11-07
@gamblor01 - Ill check it out. I have no idea what I'm doing when it comes to Linux, code or programming but I'm very interested in it. When I got my first version of windows which was 3.1 and installed it on my 386dx2 I said this is crap and for people who can't use a computer. Now I've become a Windows 7 GUI clicker so I'm very eager to re learn everything I have forgotten over the years.

@dannyboy79 - OK i formatted and followed your direction so its doing it's thing. Hopefully it will work and I will owe you many beers after this mess.

---

### Post by JoeNaz2003 on 2011-11-07
This is where I'm at and its still running. Good news is Im at about 75GB which is more than I got with Windows UFC Explorer before it stopped calculating

---

### Post by dannyboy79 on 2011-11-08
> **gamblor01 said:**
> Looks like this has pretty much already been answered but I thought I would throw in my 2 cents.  If you need to get down and dirty with the command line to copy then this post from Saikee over at justlinux.com is an excellent resource.  Specifically, read the steps in blue:


[http://www.justlinux.com/forum/showthread.php?threadid=149328](http://www.justlinux.com/forum/showthread.php?threadid=149328)




And if you need to recover data from a hard drive, here is an EXCELLENT guide for how to do that:


[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
the first link is about moving or cloning data with dd, he can't use dd as his disk is already dieing.

your second link is pretty much for hard drives where partition tables can't even be found, that's major data recovery.

for now i believe he is going to try to use ddrescue to make images of each partition and go from there on the dieing disk once he has safe images of the data saved off onto another hdd.

---

### Post by dannyboy79 on 2011-11-08
> **JoeNaz2003 said:**
> 920gb xfs partition since thats what the file system on the bad drive is correct?
i have never used XFS filesystem but from what I just quickly read, it's advantages come into play when reading and writing large files. Here's a decent write up on the pros and cons of using XFS versus EXT3. [http://www.mythtv.org/wiki/XFS_Filesystem](http://www.mythtv.org/wiki/XFS_Filesystem)

FYI= it does NOT matter what filesystem your NEW hard drive is as long as the ddrescue program can write to it. Just cause you're ddrescue'ing bytes from a XFS filesystem, means nothing as far as where you can save the image to.

---

### Post by dannyboy79 on 2011-11-08
> **JoeNaz2003 said:**
> This is where I'm at and its still running. Good news is Im at about 75GB which is more than I got with Windows UFC Explorer before it stopped calculatinglooks like it's poking away, awesome man. It's going to take a hell of a long time though. ddrescue attempts to copy byte for byte even on the areas of the disk that there is no data written to HENCE why you need the same size or larger partition for the one you're writing the image file to. Looks good man! 

one nice feature of ddrescue is the ability to stop and start the rescue process - it keeps a log of exactly what it did last so it can pick up right where it left off.

you could also cat the logfile to see any errors in it as it's running.

---

### Post by JoeNaz2003 on 2011-11-08
Its really going good now. Just woke up abut an hour ago, I left it running over night and its done with the initial scan and the first retry and on to the 2nd. It doesn't seem to have a lot of errors. Not sure exactly what the error entails though. You guys are definitely an awesome help and I hope to one day be able to lend a hand to someone as well. For now I'm reading up as much as I can.

---

### Post by JoeNaz2003 on 2011-11-08
OK it's complete. This is what I ended up with. But how do I access the image? I can't find the HDD in shortcuts.

---

### Post by dannyboy79 on 2011-11-08
> **JoeNaz2003 said:**
> OK it's complete. This is what I ended up with. But how do I access the image? I can't find the HDD in shortcuts.
> So, after the ddrescue is complete, you will need to fsck the image (or partition(s)) before you can mount them.  If for some reason you cannot remember the filesystem type you can use a tool like mmls  to find out what type of filesystem the partition is.  Lets say it is a ext3 filesystem, we will use e2fsck to fsck it: e2fsck -y /media/USB/Backup/sdb3.image — the -y will blast through the fsck answering yes to all of the block changes it will want to make.

After fsck, I then mounted the image:  mount -o loop /media/USB/Backup/sdb3.image /mnt –  to my surprise, all my lovely VMDK and VMX files were in there!  Oh glory!

So, if we apply that to your situation (as well as read about fsck from the man pages) it appears that we need to use xfs_check to check your XFS image file. Do you have xfs_check installed in that Ubuntu? If so, issuing man xfs_check should return what options you need to run to check the image FS for consistency.

---

### Post by JoeNaz2003 on 2011-11-08
yes it seems I do have it. It's xfs_check(8). I'm reading the help now to try to figure out how to use it.

---

### Post by dannyboy79 on 2011-11-08
> **JoeNaz2003 said:**
> yes it seems I do have it. It's xfs_check(8). I'm reading the help now to try to figure out how to use it.

i don't have experience with XFS so I am guessing from reading the man page but wouldn't it be something like this? actually first change the permissions of the file to read only. I believe that would be 
```
sudo chmod 444 /mnt/sdc1/sdb6.image
```
then run 
```
sudo xfs_check -f -s -v /mnt/sdc1/sdb6.image
```

[http://pwet.fr/man/linux/administration_systeme/xfs_check]("http://pwet.fr/man/linux/administration_systeme/xfs_check")

---

### Post by JoeNaz2003 on 2011-11-08
That's what I'm doing wrong I was using dev instead of mnt.
This is the error I get when running the command

joenaz@Terrance:~$ sudo xfs_check -f -s -v /mnt/sdc1/sdb6.image
ERROR: The filesystem has valuable metadata changes in a log which needs to be replayed.  Mount the filesystem to replay the log, and unmount it before re-running xfs_check.  If you are unable to mount the filesystem, then use the xfs_repair -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount of the filesystem before doing this.

Not sure what the log replayed means, or how to mount a file system. When I check the volume with disk utility it tells me its Mounted at /mnt/sdc1 and gives me the option to unmount so doesn't that mean its mounted already?

OK i read it to fast or skipped lines or something. it's mounted so I need to replay the log (not sure what that means) then unmount it and do the xfs_check.

---

### Post by dannyboy79 on 2011-11-08
> **JoeNaz2003 said:**
> That's what I'm doing wrong I was using dev instead of mnt.
This is the error I get when running the command

joenaz@Terrance:~$ sudo xfs_check -f -s -v /mnt/sdc1/sdb6.image
ERROR: The filesystem has valuable metadata changes in a log which needs to be replayed.  Mount the filesystem to replay the log, and unmount it before re-running xfs_check.  If you are unable to mount the filesystem, then use the xfs_repair -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount of the filesystem before doing this.

Not sure what the log replayed means, or how to mount a file system. When I check the volume with disk utility it tells me its Mounted at /mnt/sdc1 and gives me the option to unmount so doesn't that mean its mounted already?

OK i read it to fast or skipped lines or something. it's mounted so I need to replay the log (not sure what that means) then unmount it and do the xfs_check.Ok, you're moving really fast. I'd step back and think because you could really mess up some data. Thank gosh nothing bad happened when you were running the xfs_check against /dev/???
Ok, to be clear, your /dev/sdc1 is a hard drive you just formatted with an XFS filesystem. WITHIN that filesystem you created a FILE called sdb6.image. So you understand, /dev/sdc1 and /mnt/sdc1/sdb6.image are NOT the same thing! 

I am not sure about XFS as I already said so you will need to mount the IMAGE FILE to a folder and replay the log.

you could try this 
sudo mkdir /mnt/sdc1/image
sudo mount -o loop /mnt/sdc1/sdb3.image /mnt/sdc1/image/
you should then be able to replay the log. I don't know to be honest, as I said, I am new to XFS. 

Just take a breath and first understand everything before you run something, ask away if you're unsure.

---

### Post by JoeNaz2003 on 2011-11-08
Yea I am going entirely too fast.

Yes  /dev/sdc1 is the drive I formatted xfs and mnt/sdb6.image is the mount point of the image file I created on sdc1, right?

So should 
"sudo mount -o loop /mnt/sdc1/sdb3.image /mnt/sdc1/image/" be 
"sudo mount -o loop /mnt/sdc1/sdb6.image /mnt/sdc1/image/ ?

Also after reading the vmware tips post you linked me to, he fsck'd the image. I don't think I did that.

---

### Post by dannyboy79 on 2011-11-08
> **JoeNaz2003 said:**
> Yea I am going entirely too fast.

Yes  /dev/sdc1 is the drive I formatted xfs and mnt/sdb6.image is the mount point of the image file I created on sdc1, right?/dev/sdc1 is a linux "device". it points to your 3rd (most likely) hard drive and the first "formatted" partition. You happen to use the XFS filesystem when you formatted the first partition on the /dev/sdc hard drive. In linux you can NOT write to a hard drive until you MOUNT it to a location. So, what we did was mounted /dev/sdc1 so that it was writable at this location /mnt/sdc1/. That's maybe why this is confusing, I should have had you name that folder differently. Ok, so we used ddrescue to copy byte for byte FROM /dev/sdb6 TO a IMAGE FILE. That image FILE is called sdb6.image. It is a FILE, make sure you understand that (similar to an iso). We TRIED to run xfs_check (which is what's used for XFS filesystems instead of fsck) against the FILE. It gave you the error you posted about the log file or whatever.

From here on this is all NEW to me as well. I have never used XFS nor have I ever ran xfs_check so I don't know what replaying the log file means BUT the directions said to MOUNT the IMAGE FILE so that the log could be replayed. SO, we need to mount the IMAGE FILE.

> **JoeNaz2003 said:**
> 
So should 
"sudo mount -o loop /mnt/sdc1/sdb3.image /mnt/sdc1/image/" be 
"sudo mount -o loop /mnt/sdc1/sdb6.image /mnt/sdc1/image/ ?

Also after reading the vmware tips post you linked me to, he fsck'd the image. I don't think I did that.
OOPS, that was a typo on my part, I meant sdc6.image
```
sudo mount -o loop /mnt/sdc1/sdb6.image /mnt/sdc1/image/
```
and you're suppose to replay the log file, no idea what that means. Once the log file is replayed, I believe you're suppose to UNMOUNT the IMAGE FILE and again run that same xfs_check command you tried earlier.

---

### Post by JoeNaz2003 on 2011-11-08
OK I'm grasping it. I'm also reading the Ubuntu pocket guide which according to the forum is gonna help me understand what I'm doing better.

But onto the drive I entered the command and get a new error message:

joenaz@Terrance:~$ sudo mount -o loop /mnt/sdc1/sdb6.image /mnt/sdc1/image/
[sudo] password for joenaz: 
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Also when I go into the disk utility it says the volume is mounted. Is this different than the image being mounted?

Also when I do a file search for sdb6.logfile it finds it but I can't open it.

I've been searching to find out what replay logfile means but I'm not finding anything. Someone out there must have gotten this error.

---

### Post by dannyboy79 on 2011-11-08
> **JoeNaz2003 said:**
> OK I'm grasping it. I'm also reading the Ubuntu pocket guide which according to the forum is gonna help me understand what I'm doing better.

But onto the drive I entered the command and get a new error message:

joenaz@Terrance:~$ sudo mount -o loop /mnt/sdc1/sdb6.image /mnt/sdc1/image/
[sudo] password for joenaz: 
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Also when I go into the disk utility it says the volume is mounted. Is this different than the image being mounted?

Also when I do a file search for sdb6.logfile it finds it but I can't open it.

I've been searching to find out what replay logfile means but I'm not finding anything. Someone out there must have gotten this error.it says what volume is mounted? if you're talking about the /dev/sdc1 volume, yes that is mounted at /mnt/sdc1    

yes, that is different then the image being mounted.

i think i messed up with that last comment, post back what the results are from running these commands
```
ls -la /mnt/
```

```
mount
```

---

### Post by JoeNaz2003 on 2011-11-08
this is what I get

---

### Post by dannyboy79 on 2011-11-08
ok, from what I see from the mount command, you do NOT have the /dev/sdc1 XFS partition mounted at all. are you saying that currently without /dev/scd1 mounted you see a file within /mnt/scd1/ called sdb6.image? If so then that means it wrote the image file to your partition that is mounted to your /  folder (which is /dev/sda1).

so i want you to run the following commands

```
sudo chown joenaz:joenaz /mnt/sdc1
```

```
sudo chmod 777 /mnt/scd1
```

```
sudo mkdir /mnt/image
```

```
sudo chown joenaz:joenaz /mnt/image
```

```
sudo chmod 777 /mnt/image
```

find where the sdc6.image file is, whether it's on the partition /dev/sdc1 OR /dev/sda1. If you leave your system the way it is per the picture that I viewed that showed the results of "mount", if you issue

```
ls -la /mnt/scd1/
```

and it shows the sdb6.image then it is currently saved on the /dev/sda1 partition which is not a big deal BUT i need to know that.

---

### Post by JoeNaz2003 on 2011-11-08
OK so I tried that and it didn't work. But I just noticed that my new drive has changed to sdb1 since I have disconnected the failing drive to stop the crazy failing disk message that came up every 30 seconds and to put less stress on the HDD. But also the disk is being shown as mounted.I've tried all of the strings of code you have given me and end up with no such file or directory. Also it shows it being mounted at /media/, not sure if that's making a difference.

Do you think I should just start the whole process from the beginning and format the new drive as something other than XFS or does it have to be XFS since the original partition I'm rescuing or cloning is XFS?

---

### Post by dannyboy79 on 2011-11-09
> **JoeNaz2003 said:**
> OK so I tried that and it didn't work. But I just noticed that my new drive has changed to sdb1 since I have disconnected the failing drive to stop the crazy failing disk message that came up every 30 seconds and to put less stress on the HDD. But also the disk is being shown as mounted.I've tried all of the strings of code you have given me and end up with no such file or directory. Also it shows it being mounted at /media/, not sure if that's making a difference.

Do you think I should just start the whole process from the beginning and format the new drive as something other than XFS or does it have to be XFS since the original partition I'm rescuing or cloning is XFS?
ok, NO, don't start over. We need to try to find the image file you created with ddrescue. IF your new healthy drive is mounted do an ls -la on the folder it's mounted at to see if it contains anything.
```

ls -la /media/9a0
``` (hit tab and it complete for you)

if NOTHING but dots comes back, that means you didn't write the image file to that partition so we need to find it.

---

### Post by JoeNaz2003 on 2011-11-09
ok after running what you gave me as well as trying the entire directory string disk util gave me this is what I get. The thing I'm not grasping is if disk util shows it as mounted how come I cant find the drive anywhere. Does Ubuntu have anything like a Windows Explorer GUI with a device/directory tree? I tried searching the Ubuntu Software center but didn't really see anything.

---

### Post by JoeNaz2003 on 2011-11-09
I just got somewhere new. Since I can't seem to operate out of the Terminal yet I installed Xfe which looks like old school windows explorer. When I go to media/9a0.... I get a permission denied box with the options of "OK" or "Launch Xfe as root (Shift-F3)". I went with OK till i figure out what the other option means.

---

### Post by JoeNaz2003 on 2011-11-09
When I hover on it I get:
Modified Date: 11/08/2001 02:03:36 PM
Type: Mount Point
User: root - Group: root
Permissions: dr--r--r--

When I check Properties I get the attached image.

---

### Post by dannyboy79 on 2011-11-09
just sent you a message using AIM Express, it shows you online. you have your chat client open? it's possible it didn't go thru as i am using Firefox thru my own home ssh server as a proxy so work can't see my web traffic.

---

### Post by JoeNaz2003 on 2011-11-09
It worked. I got it

---

### Post by JoeNaz2003 on 2011-11-10
Here it is

---

### Post by dannyboy79 on 2011-12-18
> **JoeNaz2003 said:**
> Here it is

How this pan out Joe? Hope all is well with ya! Want to stay in touch if you're interested. I've been swamped, I have been truly blessed by god, fate, or both! Sent you a PM in case you didn't see this.

---

