---
title: "mount /usr on another partion"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by degarb on 2012-07-17
I got a new ubuntu install.  Already /usr is over 4 gigs and growing.

This is unacceptable.  I am guessing programs are in it.  But it doesn't look like moving any other dirs is worth the time. Yes, I will move /home.

I don't see current threads on how to move /usr to another partition.

Like a big pile of clothes piled and tangled.  I just want this /usr off the small, main drive and off to some larger, newer drive.

---

### Post by degarb on 2012-07-17
No answer....

My best guess is to sudo add to fstab:
#1. 
#UUID=0c89eb5d-ac58-46c0-b309-597b35a542e8 /home ext4 defaults,errors=remount-ro 0 1
#/dev/sdb3 /usr ext3 defaults 0 1

without comment for moving home and usr , respectively.  BUt, I don't understand uuid v. /dev/sdb3 enough to be sure.   A) I am guessing uuid would be preferred, since that will never change. (sudo blkid)  B) I don't understand  defaults 0 1 and how that might vary across systems.   C) Also, I don't understand how the googled home and usr ending could be so different.

#2. Then mkdir /media/usr and /media/home

I don't understand the cp -a and no luck googling it. 

#3. I am guessing go to root  cp /usr /dev/sdb3/usr -a   
   But I do not under stand linux drive naming enough to be sure.

Then, some googling says it cannot be done.  But some got it to work.

What am I missing?

---

### Post by degarb on 2012-07-17
rsync -avP /target_directory /destination_directory

or rsync -aS /target_directory /destination_directory

?  permissions?

---

### Post by degarb on 2012-07-17
would the destination dir be  /dev/sdb4/home or /dev/sdb4 ?

---

### Post by degarb on 2012-07-17
awaiting reply. disk space filling up fast.

---

### Post by oldfred on 2012-07-17
man is your friend if you want to understand the parameters of  a command. q is to exit from man and other commands in terminal.

man cp

I think you can copy just like you copy /home:

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

Similar to this except for home use usr and from location is not . (or home folder) but var folder.

#Format new partition:
sudo mkfs -t ext4 /dev/sdb1
sudo mkdir /mnt/newhome
sudo mount /dev/sdb1 /mnt/newhome
sudo cd /home
#copy everything in /fred (.) to newhome -a preseverses ownership & permissions
sudo rsync -rauvP . /mnt/newhome

But how small did you make / and what is filling usr? I normally make / about 25GB, have lots of programs installed and use only 7GB total including all of /home but no data. Data is in other partitions. My goal is to always have a fully functional/bootable system on every hard drive, only data may be on another drive. Then when hard drive fails I can still boot my other drive. Hopefully I am backing up data often enough that when the drive fails what data is on it is also on another drive or DVD.

---

### Post by degarb on 2012-07-17
So, what is the community feeling about moving /usr?

Off topic: not sure how to make and use script for reinstalling all applications (adding needed repos) , and porting these from one drive os to another.

(stuck with tiny primary drives until next gen computer go second hand cheap)  Though 25 megs will seem small in 2 years, necessitating another reinstall on new drive.  It is easier, more redundant, to just add new drive and move/copy program files/user docs to new drive.    Reinstalling the OS is avoided at all costs.  I am on a machine with a 2002 XP install that hasn't failed. (sliced up with ubuntu, dual boot.)

---

