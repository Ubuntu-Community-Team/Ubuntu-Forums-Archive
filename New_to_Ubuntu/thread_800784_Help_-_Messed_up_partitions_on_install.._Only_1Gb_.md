---
title: "Help - Messed up partitions on install.. Only 1Gb in /home !"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by paddyboy on 2008-05-20
Hi, I upgraded from Feisty to Hardy and while attempting to protect my dual boot options I foolishly did a 'manual' install. Now I find I only have 1Gb in my home directory. I really don't want to loose all my settings & hard work, but how can I get a sensible/normal partition arrangement ? I am petrified of the partition editor lest I kill my system.

I have put a screen shot of what gparted sees below.

I have a disk of 120Gb (total)  Win XP on Sda1 & 2 and wanted.
Not sure what SDA3 is meant to be.
Sda4 etc  is a real dogs dinner and the problem. 

How do I get out of this ? Be gentle please, I Know I messed up.

---

### Post by gnivler on 2008-05-20
> **paddyboy said:**
> Hi, I upgraded from Feisty to Hardy and while attempting to protect my dual boot options I foolishly did a 'manual' install. Now I find I only have 1Gb in my home directory. I really don't want to loose all my settings & hard work, but how can I get a sensible/normal partition arrangement ? I am petrified of the partition editor lest I kill my system.

I have put a screen shot of what gparted sees below.

I have a disk of 120Gb (total)  Win XP on Sda1 & 2 and wanted.
Not sure what SDA3 is meant to be.
Sda4 etc  is a real dogs dinner and the problem. 

How do I get out of this ? Be gentle please, I Know I messed up.

Just some observations, I doubt I'm qualified to provide an answer.  There are two ext2 partitions sda5 and sda7, both of which have no mount point but are partially occupied, do you know what's on them?  You could mount them manually to check.  It kind of looks to me like you need to destroy sda5,6,7 and 9, then resize sda8 to be the maximum size given the free space, minus a proper amount for the swap to be recreated.  That all depends on being able to remove sda5/7 though.

---

### Post by stefangr1 on 2008-05-20
You have one 3.5Gb root partition. It seems that /boot on the separate 100mb partition isn't used? Otherwise it should show up with /boot as mount point I gues. For the rest I agree with the above poster: your other ext2 and extended partitions do not have mount points so the question is if maybe they shóuld have one, or what is on them.

---

### Post by vvvladut on 2008-05-20
First of all I would backup everything that is of any importance. Just grab a few DVDs, USB drives, anything. Only then attempt to fix anything.

If you've got everything backed up, you could just wipe clean everything that's not NTFS; that would be simplest. Alternatively, get rid of the two swap partitions and of sda5, resize sda7 to fill in everything that's left of sda4, and then...I don't know. It depends on what you want to do.

If I were you, I would just wipe off everything that is Linux and do a clean install to get rid of all the mess.

Hope this helps.

---

### Post by Sef on 2008-05-20
> Hi, I upgraded from Feisty to Hardy and while attempting to protect my dual boot options I foolishly did a 'manual' install. Now I find I only have 1Gb in my home directory. I really don't want to loose all my settings & hard work, but how can I get a sensible/normal partition arrangement ? I am petrified of the partition editor lest I kill my system.

1) Did you upgrade from Feisty to Hardy directly?

2) By manual install, do you mean that you installed Hardy with a Live CD or the alternate CD?

3) It looks like Windows is not there.  Neither sda1 or sda2 have anything on them.  There is no used space on either of them.

4) It looks like you wiped out Windows or can you boot into it?

5) I would reinstall everything.  I would **back up** your data first.  

6) Another option is to check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can recover lost partitions.

7) Note on manually partitioning:  It is not hard to do, but it tricky at first.  If you want, I will help you with it.

---

### Post by forestpixie on 2008-05-20
You could probably do the moving of partitions but it could take a long time to finish, it appears that you don't have much in /home to backup as it stands and about 700Mb in other partitions. I would agree with vvvladut I think.

IF ythat's what you want to do boot with the livecd

Once it's booted into the livecd it will I expect be using the swap, open a terminal

sudo swapoff

Run gparted from the sys admin menu.

Delete all the partition sfrom inside the extended and start again, depending on how much ram you have and whether you want to hibernate I'd go for

8Gb for /
1Gb for swap 
remainder for /home

When you install and get to the partitioner section go manual, you will have a list of the available partitions, choosing the right partion for each

edit the partition - choose mountopoints

for the 8Gb mountpoint should be /
for the large partition mountpoint should be /home
for the boot partition mountpoint should be /boot

swap will sort itself.

If you decide to resize partitions I would get the gparted livecd to do it and use that. You will need to delete all the partitions apart from the / , then move / to the beginning of the extended partition, then you should be able to resize /

You probably don't need nearly 6Gb of swap though.

Edit - and sef got there before I wwrote a novel :)

---

### Post by vvvladut on 2008-05-20
> **Sef said:**
> 1) 
3) It looks like Windows is not there.  Neither sda1 or sda2 have anything on them.  There is no used space on either of them.

4) It looks like you wiped out Windows or can you boot into it?


Hi Sef. Just to let you know that I also have two perfectly working NTFS partitions that are appearing as empty in GParted. There is also that little yellow triangle. If I try to do any operation on any of the NTFS partitions, GParted spits out a dire warning that basically says that the NTFS partition is screwed up really bad and that it wouldn't touch it. 

I find that to be a great exaggeration, as XP boots up fine and Scandisk reports no errors except for one bad sector on one of the partitions, which is marked as bad, so GParted shouldn't whine about it.

---

### Post by paddyboy on 2008-05-20
Wow !! Thanks guys for all the suggestions. My head is spinning. Where to start ????

A few quick points. I know my windows is still there, as I can happily dual boot etc. Hardy was a live CD created off an iso image downloaded va another laptop. So I guess this is the way to go...reinstall.

I have since also downloaded a live gparted CD so I suppose I can blow away all the linux partitions relatively easily. 

How can I save all my nice settings e.g. desktop,spinning cube, colours, backgrounds,permissions, users  etc etc. They took ages :(

One of you kind people offered to help me with the 'manual' partition install section of Hardy. Can I take you up on that ? ....Sef I think it was. This is where my tail of woe began. 

Once again thank you **all** so much. pb.

---

### Post by vvvladut on 2008-05-20
> **paddyboy said:**
>  

How can I save all my nice settings e.g. desktop,spinning cube, colours, backgrounds,permissions, users  etc etc. They took ages :(



Come on, what would you do with your Ubuntu if all was set up and in perfect working condition? Where is the fun in that? You have to  get your hands under the hood and start tinkering with stuff to feel the fun of Linux. :)

---

### Post by paddyboy on 2008-05-20
I guess your right. I've packed up all of my toys that I can lay my hands on, and will head off into the cold wilderness of partitions.......I might be gone some time :(    pb

---

### Post by drs305 on 2008-05-20
Do you know what, if anything, you have on sda5?  If you REALLY want to save all your settings and you don't have anything on sda5, you could:

If desired, resize and reformat sda5 (and make it ext3 as a recommendation).
Move your home to sda5. 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Repartition sda 6,7,8,9 into a single partition. This will wipe out anything you have on those partitions, including ubuntu.

Install ubuntu using the space formerly occupied by 6,7,8,9 with home remaining on sda5. You would make a root ( / ) and swap partition during the install from the old, combined partitions and specify that sda5 (or whatever the new designation is) will be the home partition. You would want to make sure you tell the installation not to reformat the sda5/home partition during installation.

---

### Post by paddyboy on 2008-05-20
Well, it appears to be OK. That live CD edition of gparted is one useful piece of kit.Thanks... I recommend it to others in a similar fix. 

I followed a combination of the advice given and am pleased with the result. It now reports 40Gb ish of space in my /home dir.

gparted screenshot below.   Any of you see anything really bad on there ? If not, consider me a happy bunny.

Thanks for all your time & help. Now, to go and fix my broken toys..:(...pb.

---

### Post by drs305 on 2008-05-20
Looks good. 

There are people who will recommend you make a separate home partition. There are advantages to doing so and if you were ever to do it now would be the time. But what you have done will work very well.

Congratulations.

---

