---
title: "Raid 1 with 3 disks"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by hbost on 2008-07-08
I know the Raid question has been answered many times here before, but I have a quick partitioning question that I cannot seem to find in the forums.

I had an old Dell Optiplex lying around the house with a 160GB drive.  I reformatted the drive, installed Ubuntu Hardy Heron and realized that I could use the machine as a solid home server using Samba if I purchased two new drives and set up a RAID 1 array.

I purchased an SATA controller and 2 750G hard drives from newegg.  (Total cost of the system is now $200!)

My quick question is:  how should I partition the NEW drives for Raid 1.  There are a lot of answers in the forums using two disks but not three -- I have the option of the 3rd disk running the operating system.

Do I need:

a) boot partitions on the new drives?
b) swap partitions on the new drives?
c) any other partitions (/home, /usr, eg.) on the new drives?
d) swap partition on the 160G drive?

Any "ideal" partitioning scenario across the three disks would be appreciated.  I can reformat the 160G drive if necessary -- really have not done anything more than install Ubuntu and play with it (have my data files currently on a Linksys box using UNSLUNG -- functional, but not fast or as secure as Raid)

Many thanks.

H

---

### Post by phidia on 2008-07-08
Check out #'s 5 & 6 [here]("https://help.ubuntu.com/community/Installation").

---

### Post by umattu on 2008-07-08
So you have 

[LIST]
[*]160 GB HDD
[*]2 750 HDD's
[/LIST]

If you were to RAID 1 on these 3 drives, the 3 disk RAID 1 could only be as large as its smallest partition. It will work BUT the array would only be 160 GB's. You could add another drive to the array as a "hot spare", which in the case of one drive failing, the O.S. would rebuild the array onto the spare. But again it would need to be identical in size to the array itself.

If I was in this situation I  would do a couple things

[LIST=1]
[*]Find a new home for my 160 GB drive, (or use it to backup to)
[*]From a fresh install I would create the RAID 1 Array using the 2 750 GB drive.
[/LIST]

Once the array is built, you would then proceed with the O.S. install as you normally would. Create your partitions, mount points ... etc. RAID 1 (as I'm sure you know) is disk mirroring. What is written to one is written to all, keeps your data redundant. 

I know my post isn't exactly answering your question, but I must ask why do you want a RAID 1 setup on 3 drives?

---

### Post by hbost on 2008-07-08
Thanks.  Will check these out.

H

---

### Post by hbost on 2008-07-08
To answer umattu:

configuration is correct.  

your response is exactly what I am struggling with -- was hoping to run the operating system off of the 160G HDD and use the two 750G HDD in RAID 1 array as a separate disk used only for file storage.  therefore, the RAID configuration is on the 2 750G HDDs only and don't have the issue of 160G as the smallest partition.  

is this even possible or am i thinking too much?  ;)

H

---

### Post by darkblack on 2008-10-09
Sorry for bumping this old thread up.
Am having the same situation as of hbost

I have a 80G drive which i plan to use it exclusively to run the OS
and 2x 500G drives exclusively for data, which will be under with raid 1 mirroring. 

How do i achieve this? All the guides and walkthroughs seem to explain only setting up a raid 1 in the same disk(s) where ubuntu is installed. 

Kindly advice

The main reason i am separating the raid drives from the OS drive is that, i hope i can spindown the raid drives when there is no data activity.  The backup scripts from my other systems will write data into the raid drives only once a day and there wouldnt be much reads or writes during the rest of the day so the raid drives can be spun down to extend life and save power

Thanks

---

### Post by _sAm_ on 2008-10-09
I guess your are talking about sowftware RAID here. 

Use the Ubuntu alternate disc witch gives you the option to install on sw Raid. During partition choose the first disc for Ubuntu(without sw raid), and partition the others with sw raid1 but without installing the system on them.

---

### Post by darkblack on 2008-10-09
Thanks for your quick reply
Yes. S/w Raid.
I was hoping to install ubuntu server

Thanks

---

### Post by darkblack on 2008-10-09
Sorry for double posting. But is there a way i can create a RAID after installing ubuntu server with a single disk. Thanks

---

### Post by _sAm_ on 2008-10-09
You can install sw raid with both Ubuntu alternate and the server version.

And yes, you can install sw raid on those two disk after installing Ubuntu on the first. Linux has inbuilt support for swraid, but you also need the package called mdadm to do this. 

You can read about it here: [http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)

I dont know how to do it, but if you google mdadm + ubuntu 
I guess you will find plenty.
Here is one: 
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

