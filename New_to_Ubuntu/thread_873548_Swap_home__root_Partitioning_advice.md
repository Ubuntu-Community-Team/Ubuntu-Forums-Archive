---
title: "Swap /home / root Partitioning advice"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by waspbr on 2008-07-29
k, I kinda always wanted to look into this but due to my busy schedule I never got the chance. So I was wondering about partitions in linux... I know that a hard drive can only have a maximum number of 4 partitions right?


when installing a linux Os we need to create a swap partition right, that's one, the you have your root partition (/), so 2 down... since some of us (me) dual boots then three of the partitions are used... then if you want to create a /home partition then you'd have to use the remaining one right? but is that all?

I am asking this because I kinda got used to dristo hopping,trying out some distros and all, atm on this laptop I have a single harddrive where  I crammed vista, ubuntu hardy, ubuntu intrepid and the mandatory swap.

unfortunately getting rid of vista is not realistic for me, and having a /home partition would be nice since all files would be in one place and I wouldn't need to have duplicates or have to keep copying files from one part. to another.

So my question is would it be possible to fit a /home partition here in this vista|swap|linux|linux setup or should I just get over it?

---

### Post by northern lights on 2008-07-29
> **waspbr said:**
> I know that a hard drive can only have a maximum number of 4 partitions right?Wrong. A hard drive can only have four _primary_ partitions. The extended partition can host a basically infinite number of logical ones.


> **waspbr said:**
> So my question is would it be possible to fit a /home partition here in this vista|swap|linux|linux setup or should I just get over it?
Nope, don't have to get over it. It's more than possible to create a separate /home also.
Windows wants to reside in the first partition of a drive, otherwise it requires extra tinkering to get it running. Apart from that you can do as you please.

---

### Post by Elfy on 2008-07-29
Indeed - although I was under the impression that there is a finite number of logicals you can have - but it's not small.

When I have a new drive I tend to set it up with 1 of each primary and extended but not use the whole drive - then I can add more primaries if I so wish or resize either.

---

### Post by deanjm1963 on 2008-07-29
I have a 500gb HD for linux, I went whole hog and did the full partitioning scheme.

root = 4gb
usr = 8gb
var = 8gb
home = 14gb
dean = 70gb
work = 70gb
video = 110gb
misc = 70gb
storage = 130gb
tmp = 14gb
swap = 2gb

I know that some of those system partitions are excessive, but for my setup it works well. I have a fairly small /home partition as I prefer to keep my working files well out of systems' reach. My /storage partition contains not much more than Ubuntu/Kubuntu CD/DVD isos, a copy of my fonts, text files that contain apt sources for medibuntu and scribus, and 3rd party debs. I also keep a weekly backup of my work on there.

Depending on how large your HD is, think about partitioning properly, it can save a lot of grief later on if you upgrade or change distro.

---

### Post by rolnics on 2008-07-29
Yeah windows is a pig when it comes to partitions, it's only ever happy on the first partition of any hard drive. Before linux I had my 2 hard drives booting XP one was for just anything especially games and the other was setup with minimal stuff installed which I used for creating music. Then I had several separate partitions after them to keep things tidy and for ease of backing up purposes.

I never had a problem with the number of extended partitions.

Have you thought of buying an external hard drive to use for your /home?

---

### Post by Sef on 2008-07-29
How big a swap partition should be depends on your ram.   512 mb ram and under swap should be 1 1/2 - 2 times ram.  More than that 1 GB swap is all you should need.  If you have at least 2 GB ram, then you can have a 1 GB swap, but it is not really needed.

For your partitions, you should have something like this:

Vista/XP - 15 - 20 GB
Ubuntu - 8 - 10 GB
Swap - 1 GB
Home - the rest.  For Home you can make it either as NTFS or ext2.  If you make it NTFS, then there is a download from the Ubuntu repositories that you need, so it can be written to by Ubuntu.  If you make it ext2, then Windows needs some additional software, so it can write to it.

---

### Post by Bachstelze on 2008-07-29
> **Sef said:**
> How big a swap partition should be depends on your ram.   512 mb ram and under swap should be 1 1/2 - 2 times ram.  More than that 1 GB swap is all you should need.  If you have at least 2 GB ram, then you can have a 1 GB swap, but it is not really needed.

unless you plan to use hibernation, of course.

---

### Post by rolnics on 2008-07-29
> **Sef said:**
> 
If you make it NTFS, then there is a download from the Ubuntu repositories that you need, so it can be written to by Ubuntu.

I love this forum you always learn something new!

---

### Post by vanadium on 2008-07-29
You should not share one single home partition with different Linux distro's. What you can do, though, is to have one common partition for your user data (documents, images, etc.). Using symbolic links, you can then conveniently access the data from within each Linux installation.

You can keep that partition in ext3, and use the Windows ext2 driver to access the data from within MS Windows.

---

### Post by northern lights on 2008-07-29
> **forestpixie said:**
> Indeed - although I was under the impression that there is a finite number of logicals you can have - but it's not small.Fair enough, you're obviously right.

The maximum device number for a sata disk is 16. Since the drive itsself uses up a device name (hda or the like), there can be 15 partitions inside. Leaves 3 primaries plus the extended partition (which itsself is primary) with up to 11 logical ones inside.

For pata the numbers are 64/63/59/3/1 respectively (still 4 primaries)

---

### Post by waspbr on 2008-07-29
thanks for the replies,  I did leave out the "primary"on purpose hoping I would get a lecture about it, but it seems clear anyway... So if I were to create a new /home partition it would have to be a logical one. I still think that the difference between primary and logical partitions are a little fuzzy to me, think I am gonna wiki it.

Guess using having a /home partition in a usb device would not be great cos I would have to carry it around and it might be a hassle, though it maybe a good idea for my desktop...

My HDD is average size, or biggish for a notebook apparentlhy, 250 GB, 100 of those are devoted to my vista partition which I barely use (only when I must at work), though 25Gb is taken by my music folder and 40 are free. 

I made my swap 4GB big,twice my RAM,  but the ironic thing is that I cannot suspend/hibernate (drivers issues), the rest is divided amongst two linux partitions of similar size ~70Gb. 

gonna give this some thought before I do anything...

---

