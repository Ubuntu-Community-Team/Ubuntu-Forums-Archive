---
title: "create mount point to access external hard drive"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by rpete on 2008-10-13
I am changing computers (giving the old Windows XP based one away).  I have all my old files and programs backed up on an external hard drive.  I connected it to my new Ubuntu based computer through a USB connection.  The drive is recognized but when I click on it to access the old files I get the message "cannot mount volume."  I went to the terminal and typed in the recommended command but it didn't work.  It seems I have to create a mount point. Could anyone walk me through how to do that? 

A broader question: Is  this the best way to transfer files and programs? If I have the entire hard drive from my old computer backed up on an external hard drive will I be able to pick and choose which files and programs to transfer to the new computer?

---

### Post by jbrown96 on 2008-10-13
To mount you need to do a couple of things
1. find the drive
```
sudo fdisk -l
```
your external will probably only have one partition and should report the size of the drive. Remember something like /dev/sda2, /devsdb1, etc
2. create a mount point
Personally I like mount points in my home folder, but drives are automounted in /media. Do one of the following (and you can change the name too)
```
mkdir ./external
```
```
sudo mkdir /media/external
```
3. Mount the drive based on what you provided earlier
```
sudo mount -t auto /dev/sdb1 ./external
``` be sure to change /dev/sdb1 and ./external to what you did in the previous steps.
4. Not sure about the problem that you were having but it may be because the drive is "dirty". If the previous command fails try ```
sudo mount -t auto /dev/sdb1 ./external -o force
```

---

### Post by rpete on 2008-10-14
Hi, Thanks jbrown96.  I was able to find the drive.  It is /dev/sdb1  but I failed to create a mount point.  I'm not sure if you meant that I should type in the second step command exactly as you wrote or that I should change <external> to <MyBook> so the creat a mount point command would read: <sudo mkdir /media/MyBook>    

I did type that last line and got <cannot create directory Media/MyBook file exists >  

In your step 3, you state I should mount the drive based on what I provided earlier.  What does this mean?  Does this mean I should use the drive location /dev/sdb1 and the name MyBook in the command?

I then typed <sudo mount -t auto /dev/sdb1 ./MyBook> and got the message 
that this didn't work, failed to mount because <NTFS is marked to be in use>  

I then tried the command <sudo mount -t auto /dev/sdb1 ./MyBook -o force>

I got the message <LogFile indicates unclean shutdown (0 0)> and that I should reset LogFile.

Any help would be appreciated.

---

### Post by rpete on 2008-10-14
Jbrown96--I think the message in the terminal that finally struck me was "File exists"  I am able to access the external drive through my new computer.  It works. Thanks again for the help.

rpete

---

