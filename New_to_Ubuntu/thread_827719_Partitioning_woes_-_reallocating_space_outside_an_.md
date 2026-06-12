---
title: "Partitioning woes - reallocating space outside an extended partition?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by vavroom on 2008-06-13
Hello all,

I hope you'll be able to help.  I've searched and read the forums but can't seem to find the answer I am looking for.

I installed Ubuntu on my laptop, dual booting with Vista (yeah yeah, I know, but I have my reasons...) about a year ago.  I have misplaced my notes as to exactly which partitions are which and why I set them up as such, but I remember there was method to my madness (some from reading up on this forum and community help site).

Ok, the problem:  The partition where Windows is installed is horribly short on space.  The obvious solution is to take unused space from a data partition and allocate it to the Windows partition.  So far so good.

I used the LiveCD and fired up GParted.  It gave me the following information:

unallocated 1MB
/dev/sda1 10GB (NTFS) - 4GB used
/dev/sda2 30GB (NTFS) - 27GB used (boot)
unallocated 6GB
/dev/sda3 10GB (ext3) - 6GB Used
/dev/sda4 50GB (extended) - 
    /dev/sda5 2GB (linux-swap)
    /dev/sda6 48GB (fat32) - 28GB used

I am not sure what sda1 is.  I *think* it's the home partition for Ubuntu, but I cannot think why I would have done that and leave it as NTFS.

sda2 is the windows partition I am trying to grow.

sda3 is (obviously?) where I've installed Ubuntu

sda4 is an extended partition, which contains the swap (doh!) and the data partition I wanna shrink.

So far so good.  I am able to reduce the size of sda6.  But the free space remains in sda4, and is not available to tag on to sda2.

I suspect it's a problem with me not being able to use the software properly, but after trying to figure it out for several hours, and not wishing to do something stupid (like destroy the data, etc), I'm not sure what to do next.

Any assistance would be greatly appreciated.

---

### Post by tysonh on 2008-06-13
I use a laptop with a 60g drive and I have xp and ubuntu 8.04 dual booted as well.  I didn't as many partitions as you did.  I've seen how to's where people have a similar set up as you.  All I did was shrink my windows partition so half my drive would be for xp and the other half ubuntu.

I didn't make exactly half because I accounted for how much space windows had used already and how big I was going to make my swap file.  So basically I made it 50/50.

So, in short I'd say get rid of all those partitions and just use a ntfs partition for xp and ext3 for ubuntu and a swap file I don't mess with the other stuff because I've never had a need for them.

---

### Post by hyper_ch on 2008-06-13
well, sda4 is an extended partition and sda6 is a logical partition within sda4... so by altering sda6 you give free space to sda4.

As sda4 and sda2 are no next to each other you can't give that space directly there.... not even sure if you should give it first from sda4 to sda3 and then from sda3 to sda2.

Are you sure you need sda6 as fat32? Or why do you want to move space anyway?

---

### Post by Sef on 2008-06-13
> I suspect it's a problem with me not being able to use the software properly, but after trying to figure it out for several hours, and not wishing to do something stupid (like destroy the data, etc), I'm not sure what to do next.


First, **back up** your data.

Second, you will end up reformatting your Vista and data partitions, so you will need to reinstall Vista and your data.  

Third, next time you want to check your partitions in Ubuntu do it this way:

Applications > Accessories > Terminal

then type or copy and paste in this code:

```
sudo fdisk -l
``` Small L.   Copy and paste the results here.

---

### Post by vavroom on 2008-06-13
@Tyson, the data partition (sda6) is where I keep my data.  I have it on a different partition so it can be more easily backed up, or other partitions reformated without losing data.  the Ubuntu /home partition is a bit similar in concept.

@hyper, thanks for the response.  If I remember from last year, sda6 was set as fat32 so it could be easily accessed by both Ubuntu and Windows.  

I need to move the space to sda2 because sda2 is running out of space and Windows is yelling at me (well, performance issues and all that with less than 10% free space on it).

So, how would I move the free space created in sda4 outside of it and to sda2, or sda3 if I have to take it in steps?  I guess that's the bit that eludes me at the moment.

---

### Post by hyper_ch on 2008-06-13
I'd say you'll have to do as Sef said: Resetup your computer...

Fat32 partitions aren't needed anymore. With ntfs-3g you can easily read/write to ntfs drives. With the ext2/3 drivers from [http://www.fs-driver.org](http://www.fs-driver.org) you can easily read/write ext2/3 partitions in windows.

---

### Post by vavroom on 2008-06-13
Thank you for the tip on fdisk, indeed much easier :)

> **Sef said:**
> 
Second, you will end up reformatting your Vista and data partitions, so you will need to reinstall Vista and your data.  


Ack!!!  That's not really an option I'm afraid.  Reformatting Vista means having to also reinstall and reconfigure software, etc.  I'm not in a position of being able/willing to waste several days doing that.

Is there really no option around that?  Seems like it shouldn't require a reformatting to move free space from one partition to another?

---

### Post by Sef on 2008-06-13
> Ack!!! That's not really an option I'm afraid. Reformatting Vista means having to also reinstall and reconfigure software, etc. I'm not in a position of being able/willing to waste several days doing that.

Is there really no option around that? Seems like it shouldn't require a reformatting to move free space from one partition to another?

The only way around reinstalling would be if you [cloned the OS]("http://clonezilla.wiki.sourceforge.net/") (and the data if you wanted) to another partition or hard disk.

---

### Post by sam_delta on 2008-06-13
sda1 looks like the system recovery partition??? not sure tho

to reallocate unallocated space from a extended partition to a primary 

you need to shrink and make sda4 smaller, you can do this with the live cd, BUT make sure you un-mount your SWAP, because gparted wont let you resize the whole extended if theres 1 of its partition mounted (yes, the live cd actually uses your swap, so turn it off)

also, check out this link (i dont know how helpfull itll be, ill read it later on)
[https://answers.launchpad.net/ubuntu/+question/30332](https://answers.launchpad.net/ubuntu/+question/30332)

sam

---

### Post by ByteJuggler on 2008-06-13
What you want to do is probably possible but with a lot of jiggery pokery, so do not proceed until you've got a verified backup of everything.  You'll have to shrink/move all the partitions above the one you're trying to grow so that the free space ends up at the end/next to the partition you're trying to grow, e.g.

Now:
[[sda1 - 10GB][sda2 - 30GB][xxx6GB freexxx][sda3 - 10GB]
 [sda4 - extended 50GB [sda5 2GB][sda6 - 48GB]]
]

Will probably first change to 

[[sda1 - 10GB][sda2 - 30GB][xxxxxxxx16GB freexxxxxxxx][sda3 - 10GB]
 [sda4 - extended 40GB [sda5 2GB][sda6 - 38GB]]
]

Which means that sda6 will need to shrink first then move right, then sda5 will move right, then sda4 (the extended partition) will have to be redone so its start moves right, then sda3 will move right, which leaves the free space next to sda2, ready for you to expand into.  From experience I can tell you that all this partition moving is going to take ages when just done with e.g. gparted.

BTW, I notice you have 6GB of free space there already.  Why don't you expand into that?  Or is that not enough?

Another suggestion: Get a new disk instead, and mount the new diskspace in your existing Vista tree somewhere (e.g. move Documents and Settings or whatever's taking the space onto the new drive, then mount it in it's original location on Vista, thus effectively giving you new space without requiring any repartitioning.

Another suggestion: Get a new disk, and clone the linux partitions onto it, setting your system up to use them instead of the original ones.  Once the clones work properly etc, delete the originals from the original disk, and then grow the Vista partition into the now freed up space.  

Personally I'd go for this last option (and indeed, has done similar things several times in the past), as it avoids a heck of a lot of moving partitions jiggery pokery, that can take ages on a single disk. (Imaging operations between different physical disks are by comparison very very quick and relatively painless.)

---

