---
title: "Partition Image - disc full error"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-08-22
I am trying to backup the partition with Ubuntu on it so that I preserve all the sweat and tear that I have so far invested to get Ubuntu up and running as I like. I would hate to loose it all and have to go back to scratch to set it all up again, but it would be a good repeditive learning exercise.
I believe that Partition image with is a tool on the PartedMagic boot cd will do this but I cannot make it work.

I have 3 partitions on my HDD (not counting the SWAP partition)
I used to have windows set up like this and it worked well for me.
OS on one partition, another partition devoted to images of the OS partition, and a 3rd and largest for my data.

At the moment:
sda1 is my OS partition
sda3 is m data partition and 
sda4 is waiting to be used as the backup image partition.

Problem is that in Partition Image, whateve path I put it for the disc image to be written to, always comes back with a disc full message. Sometimes it comes immediately, and on other attempts it will work for a few seconds and then come.

There is plenty of space on this partition so I wonder what is wrong.

Can someone help me with this simple task

---

### Post by kk0sse54 on 2008-08-22
Run Gparted and make sure you have enough free spacefor the disc image as it might just be that the partition is too small

---

### Post by steinzeitmensch on 2008-08-22
I have done this and can see that I have 30Gb free here.
I have a feeling that I am just messing up the path to this partition and in the end trying to write the image (of sda1) back onto the same partition (sda1)
I do not know what path to use.

---

### Post by kk0sse54 on 2008-08-22
Are you typing /dev/sda1? Through Gparted you can see the path to the partition which is usually /dev/sda or /dev/hda plus whatever number that partition is.

---

### Post by steinzeitmensch on 2008-08-23
I looked again at the Gparted. There is a screenshot of what I get.
So I tried to put in the location as per Gparted in Partiton Image (See the other 2 screenshots) and still 'no cigar' ](*,)

What am I doing wrong?:(

---

### Post by kk0sse54 on 2008-08-23
Sorry mate I don't see any screenshots. Just make sure that you are saying exactly /dev/sda1 to copy to /dev/sda4 (or hda depending on your path) and if the backup partition is ntfs you might want to defrag it if there's been plenty of data on it before. The only other thing I can think of right now is to make sure you don't have a corrupted CD, that you checked the iso when you downloaded it and you didn't burn it too fast.

**Edit: you might want to check out their forums [http://partedmagic.com/phpBB3/viewforum.php?f=7](http://partedmagic.com/phpBB3/viewforum.php?f=7) and post your answer there, right now I'm searching their website for your problem

---

### Post by steinzeitmensch on 2008-08-23
I totally forgot to add the screenshots.
Offcourse my post makes no sense without them.
Here they are now.

BTW
The partition is ext3 and it is completely clean and formated at the moment.

---

