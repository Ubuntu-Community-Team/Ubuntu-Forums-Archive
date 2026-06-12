---
title: "Oneiric's &quot;reccommended&quot; backup program?"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by RayArdia on 2012-02-22
Since having experienced a major hiccough when trying to use Déjà Dup I have been trying to fathom out what is or isn't the bee's knees regarding the vexed questions 'What to back up?' 'How often?' and the most important one - 'which Backup program?'
Despite the fact that everyone needs to be able to recover from a mishap in which files get lost or corrupted, and even though Linux and its derivatives have been in worldwide use for donkey's years we would as yet appear not to have a reliable, GUI-usable backup system.
Like many others I want to spend the minimum time tweaking my system. I appreciate the versatility of the Command line and use it (often with the help of clever members of the Ubuntu community, for which my thanks), but I don't want to run the risk of screwing up something as important as a backup by a miss-place punctuation mark in a command.
I checked out Déjà Dup before using it and two small trial backups seemed to go well, so I went ahead with a full backup.
Now I find that I am unable to restore my data. Its loss is unlikely to impact badly on the civilised world - but it IS important to me.
I have asked a question in Lanchpad (#188112)and opened a thread in Beginner's Talk but no helpful replies as yet.

---

### Post by cottfcfan on 2012-02-22
Clonezilla - for a full disk or partition copy.
Luckybackup or Backintime - for data backup.
There are countless others, but i have backed up & restored succesfully from all 3 of these.

---

### Post by joetait on 2012-02-22
I don't know if you have found this already, but it may be helpful: [https://help.ubuntu.com/community/jmburgess/Backup#Graphical_User_Interface.28GUI.29_Based](https://help.ubuntu.com/community/jmburgess/Backup#Graphical_User_Interface.28GUI.29_Based)

---

### Post by RayArdia on 2012-02-22
> **cottfcfan said:**
> Clonezilla - for a full disk or partition copy.
Luckybackup or Backintime - for data backup.
There are countless others, but i have backed up & restored succesfully from all 3 of these.

Thankyou Cottfcfan. I'd heard of Clonezilla but not the other two.
Interesting, but simply adds to the problem 'Which to choose?' doesn't it. How is a novice (Ubuntu-wise, ceratainly not in age!) to know which is best - other than plumping for the one carried along by his Ubuntu distro. THAT one must be the best ............surely? As for my problem - still unsolved!

---

### Post by RayArdia on 2012-02-22
> **joetait said:**
> I don't know if you have found this already, but it may be helpful: [https://help.ubuntu.com/community/jmburgess/Backup#Graphical_User_Interface.28GUI.29_Based](https://help.ubuntu.com/community/jmburgess/Backup#Graphical_User_Interface.28GUI.29_Based)

Thanks Joe, no I hadn't seen that advice but I think that even if I had've read it I still would have had to throw dice to decide which to choose - and if I'd chosen Déjà Dup I'd have got myself a problem - like I have done!

---

### Post by roelforg on 2012-02-22
If you've got a backup-hd of the same size of your main hd or larger,
You could do either of these 2 (assuming the main hd = /dev/sda and the backup hd=/dev/sdb):
If they're the same, you could raw-copy the content of 1 hd to the other (dangerous, will erase hd2):
```

sudo dd if=/dev/sda of=/dev/sdb

```Or if larger, you could fill it with a partition and have it filled like this (hd2 mounted on /media/backup ---DANGEROUS):
```

sudo dd if=/dev/sda of=/media/backup/image.img

```

These commands create a copy that's 100% the same.
BUT they're all VERY DANGEROUS!!!

---

### Post by RayArdia on 2012-02-22
Thank you, but your warning that the command "might be dangerous" put me right off!
If it's just a plain ole' copy I'm trying to acheive, I already have it in /Tmp. See my thread "Deja Dup fails to restore".

---

### Post by roelforg on 2012-02-22
> **RayArdia said:**
> Thank you, but your warning that the command "might be dangerous" put me right off!
If it's just a plain ole' copy I'm trying to acheive, I already have it in /Tmp. See my thread "Deja Dup fails to restore".
The last one won't hurt you, the point is just that anything utilizing dd is dangerous,
it's full name is Data Destroyer for a reason.
It's argument handling system is very sensitive, one typo and it might erase your HD.

When used correctly, it can be your best tool to backup data;
no backup beats an 1-1 image of the HD.

---

### Post by mastablasta on 2012-02-22
do you want automatic backups or you plan to do them manually? if you plan to do them manually then cloning with tool like Clonezilla is best. though it might be easier to use redobackup as it's interface is much simpler and more user friendly. it will check the created image to make sure backup went well and that restore is possible.
 
another interesting manual backup option is mintbackuptool. 
 
but if you want to synchronise you disk to another disk on some schedule you would need to use something like rsync or its GUI grsync.
 
another (and probably true backup) option is to use RAID disk array.

---

### Post by RayArdia on 2012-02-22
There! See what I mean, mastablasta has just added ANOTHER 3 or maybe 4 runners to the 'which program' field!
I do believe that what we ALL (clever folks as well as dumbos like me) need is a Ubuntu-approved,reliable Backup program, with a GUI to make it foolproof in use.
What __I__ need right now is a solution to restoring my data!

---

### Post by larrypg on 2012-02-22
Hello,

I have a feeling that your original question was how do you restore from a backup made with deja dup but it was lost in all the other stuff.  I do not have the answer but if those who do were to read this topic they would think it is about what program do you recommend...not how to restore from a backup you already made.  Just my two cents.

---

### Post by Zill on 2012-02-22
The difficulty is that there is no "one size fits all" solution to this problem.  Each computer user has different requirements to another, with different configurations of hardware, software and data.  In addition to this, the perfect "bug-free" program has yet to be written!

All I can suggest is for you to carefully define *your* requirements, then search out programs that *may* do the job.  Having made a short-list, read up all the reviews and comments on each one to find out where the pitfalls are.

Finally, try out a few programs with "dummy" data and see if it does what you want.  After all this, you should end-up with a backup application that works for *you*. :-)

PS.  FWIW, I currently use Simple Backup but am considering changing to Lucky Backup.

---

### Post by scrooge_74 on 2012-02-22
After many times losing data for different reasons, I settle on the following.

I have a couple of laptops (mine for work and stuff, and the kids laptops) my backups all go to a small server I have at home that has a 4 disk RAID 10 array.

So far I lost one disk one time so I only had to go and purchase a replacement and all my data stayed safe

As for an app I just use rsync

---

### Post by cottfcfan on 2012-02-23
Hi Rayardia..
I see what your problem is now, ive been messing with dejadup for the last 10 minutes doing dummy backups of small files, and when I try restoring them back to my home folder, the retored files aren't there, also the files seem impossible to hack. This does seem a complicated program to use in a default install. With luckybackup, if all else fails, you can just copy & paste the files back again.
I can't help you with your problem, but I hope someone else on here can.


Edit...
Actually this has caused me more problems than I realized.
After attempting to restore a music file to my home folder, I now seem to have lost the ability to "delete" anything in my home folder.
So I logged out and after attempting to log back in, I have the message "could not update ICEauthority file /home/user/wayne/.ICEauthority".
Have tried many "fixes" but nothing allows me to login.
Seems Dejadup has hosed my system.
Good job I dual boot with Xubuntu, otherwise i'd be screwed.

---

