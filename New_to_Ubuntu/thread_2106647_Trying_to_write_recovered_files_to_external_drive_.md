---
title: "Trying to write recovered files to external drive in Photorec"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by necron_99 on 2013-01-19
I am running a Rescue Remix CD and have a 250GB NTFS external drive--I need to write any files Photorec recovers to it. Trying to recover files from a deleted 220GB partition. It does list the external drive as one of the media from which I can recover. but at the next screen I don't see an option to write to it--Photorec asks if I want to write to home and or to these directories:
drwxr-xr-x  999 999 160 .
drwxr-xr-x 0 0 60 ..
-rw-r--r-- 0 0 40960 photorec.ses

I looked online and it seemed like I needed to format the drive as FAT32. I used guiformat to do that on my Windows partition. The same options appeared. Is it one of the above? If not what do I do?

---

### Post by fanum on 2013-01-19
It does not matter if it is NTFS formatted the problem is you will need to move to the directory from the current directory you are in (a terminal session always starts in the "Home" directory. 

There are two ways to do this, you can navigate to the /media folder, by selecting ".." as that designates "go up a folder closer the the root of the hard drive". Your external will be in a folder in the "/media/" folder. An example:

You are here (your home directory):

/home/ubuntu/ 

so one ".." will take you to:

/home/

and another will take you to the root of the drive or:

/

You can then select the "media" folder, then your external drives folder. 

Which will take you to:

/media/NAME OF EXTERNAL

A second way to get around this is to run photorec from the commandline once you are already in the directory you want to save to. Here is an example of the commands I would run to get to my external and run photorec (one per line). 

cd /media/MYEXTERNAL/
photorec  

-FANUM

---

### Post by mapes12 on 2013-01-19
I've not tried it but I suggest formatting your external HDD to a native linux format such as ext4. NTFS and FAT are Microsoft partitions. Rescue Remix is native Ubu which means that no other support should be needed to recognise the drive.

---

### Post by fanum on 2013-01-19
> **mapes12 said:**
> I've not tried it but I suggest formatting your external HDD to a native linux format such as ext4. NTFS and FAT are Microsoft partitions. Rescue Remix is native Ubu which means that no other support should be needed to recognise the drive.

Do not do that. You will be unable to access the files on Mac or Windows if you do. FAT is universally used, the only time to change that would be if you need files larger than 4gb.

---

### Post by fanum on 2013-01-19
And NTFS read/write drivers have been stable in Linux for years, so that can be used also if you need to store files larger than 4gb. There are certain programs that have limitations that require a native Linux file system to operate, however saving to FAT/NTFS is almost always supported (because Ubuntu and other Linux distributions support them).

---

### Post by mapes12 on 2013-01-20
I think the OP needs to add some clarity here. My reading of the question is that the OP has the target drive for the backup formatted to NTFS. I have had issues with target drives formatted to NTFS which have been solved by simply changing the format config to ext(x).

Nobody is suggesting formatting the drive containing the data that needs to be recovered.

Good luck ):P

---

### Post by necron_99 on 2013-01-20
Thanks everybody. I have the external drive formatted now as NTFS again. It shows up via the df command. However, in /media it's not clear how to designate it--I've run Photorec several times but it doesn't seem to be saving to the right place. (I hope I haven't done any more damage.) I see options to write to usb0 through usb7 but I don't see how to know I'm choosing it. I have used usb0. I'll try formatting it as ext4 and see if it matters.

Edit: doing this in /media as instructed. Thanks again.

---

### Post by fanum on 2013-01-21
> **necron_99 said:**
> Thanks everybody. I have the external drive formatted now as NTFS again. It shows up via the df command. However, in /media it's not clear how to designate it--I've run Photorec several times but it doesn't seem to be saving to the right place. (I hope I haven't done any more damage.) I see options to write to usb0 through usb7 but I don't see how to know I'm choosing it. I have used usb0. I'll try formatting it as ext4 and see if it matters.

Edit: doing this in /media as instructed. Thanks again.

It will be in /media/YOUR DRIVE/ not just the media folder (Where Your drive is the name that shows up, usually the only folder).

You can also run the "mount" command to see where it is mounted

---

### Post by fanum on 2013-01-21
> **mapes12 said:**
> I think the OP needs to add some clarity here. My reading of the question is that the OP has the target drive for the backup formatted to NTFS. I have had issues with target drives formatted to NTFS which have been solved by simply changing the format config to ext(x).

Nobody is suggesting formatting the drive containing the data that needs to be recovered.

Good luck ):P

Photorec has no limitations on NTFS. He/she is just havinging a hard time navigating the filesystem to find where the external is mounted. Formatting to ext2/3/4 will make the data recovered useless to every operating system (Windows and mac). I do not recommend it, since it is not the issue.

---

