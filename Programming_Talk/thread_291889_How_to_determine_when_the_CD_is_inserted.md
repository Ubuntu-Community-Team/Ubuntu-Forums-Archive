---
title: "How to determine when the CD is inserted?"
date: 2006-11-03
forum: Programming Talk
---

### Post by DeeKey on 2006-11-03
I am writing a script to automatize the process of creating one 4,7 GB DVD from mini DVD (8 cm).

Manual process looks like the following:

1) insert mini DVD to the drive;
2) copy its content (/video_ts/*.vob) to hard drive folder
3) eject CD/DVD
4) go to step (1)

Automatic process could be done that way. I am writing a BASH script. Here is how do I see this automation process:

1) determine that DVD is inserted 
2) cp /video_ts/*.vob /home/user/DVD/Disk_i
3) eject
4) i++;  go to step (1);


Here is my scratch script :) 

##!/bin/bash

for i in 1 2 3 4;  do 
  # How to determine if the CD/DVD is present?
  DVD_Source='/media/cdrom/video_ts/*.vob'
  DVD_Destination='/media/sda9/DVD/Disk'
  mkdir $DVD_Destination$i
  cp -i $DVD_Source $DVD_Destination$i
  eject

done


So my problem ](*,)  is HOW to automatically determine if the CD is inserted to the drive? What command to use in bash to do it?

---

### Post by PriceChild on 2006-11-03
*thread moved*

---

### Post by 3rdalbum on 2006-11-03
I'm not sure about exactly how to do this in shell scripting, but I would cd to the DVD's mount point, ls, and then check that some characters are returned as a result. If there is a non-empty DVD in the drive, the ls command will return nothing.

---

### Post by DeeKey on 2006-11-06
Thank you for your help! I have made it!

Later I will post my script here.

Now I am figuring out how to split vob file which is actually a mpeg 2 file so that it will fit on DVD (4,3 GB). I have searched both in Google and in Ubuntu forums... Still do not know how to do it the best way.

---

### Post by Houman on 2006-11-06
hi there, 

Why dont you rip the DVD (convert it to mpeg4) so that you can same some space, mencoder does that for your I think (its the encoding part of mplayer)

regards

Houman

---

### Post by DeeKey on 2006-11-06
The reason I do not use any ripping software is that I want to put video back to DVD :)

---

