---
title: "how big should /root be?  /boot?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-06-04
Installing 8.04 (Hardy Heron) on 250 Gbyte hard drive.  How big should the /boot and /root partitions be?  I. E., are there rules of thumb for these 2 sizes?

Thanks

---

### Post by aeiah on 2008-06-04
i dont have a separate boot partition but my root partition is 11.5GB and i have 7GB free. it depends what kind of software you're going to be using, but really, a lot of the big stuff gets installed to your home partition anyway (games, virtualbox images etc). id say 10GB

---

### Post by dracayr on 2008-06-04
no, but you don't need much disk space for them. How much diskspace /root needs, depends on your administrator (presumably you). /root is kind of the home directory of root. /boot needs about 100MB (at least on my comp). In any case, you most likely will not need a seperate partition for them.

@aeiah: I don't think he means the root filesystem, but rather the folder /root/

dracayr

---

### Post by ibutho on 2008-06-04
I personally don't see the point of having a separate /root partition (unless you meant root as in /). You don't use the root account very often (in Ubuntu by default, you can't even login as root) to warrant /root being on a separate partition. As for the size of /boot, its variable depending on the number of kernels you wish to install, but 200MB should be more than sufficient for a couple of kernels (my /boot on Ubuntu uses 35MB using one kernel).

---

### Post by Duck2006 on 2008-06-04
> **raymondvillain said:**
> Installing 8.04 (Hardy Heron) on 250 Gbyte hard drive.  How big should the /boot and /root partitions be?  I. E., are there rules of thumb for these 2 sizes?

Thanks

You only need a / root partition and a swap partition, for ubuntu.

10Gb for root partition
1Gb  for swap partition

If your using a LVM install then round 100Mb at the start of the drive will be ok.

---

### Post by sayakb on 2008-06-04
@OP
You can create 3 separate partitions: /, /home and swap. You don't need a separate /root or /boot

/ = 10GB
swap should be >= size of your RAM
/home = remaining hard drive

---

### Post by Duck2006 on 2008-06-04
> **LinuxIsInnovation said:**
> @OP
You can create 3 separate partitions: /, /home and swap. You don't need a separate /root or /boot

/ is / root partition.

---

### Post by jjgomera on 2008-06-04
well, with /root i think he is thinking about /

i have:
/ 8GB used, 10GB total (with fairly software installed)
/boot 30MB used, 100MB total (useful is you used to install distro often)

---

### Post by ibutho on 2008-06-04
Disregard. I misread on of the posts.

---

### Post by pancakelizard on 2008-06-04
if you have a seperate root, swap and home partition which partition gets the os and all programs, drivers, etc?

following the above posts and having a 160 gig drive and 6 gb of ram would the following be a waste for root?

swap - 6 gb
root - 30 gb
home - 124 gb

would it be a waste to make swap 10 and home 120 keeping root at 30?
is root basically only the system files?

---

### Post by Golem XIV on 2008-06-04
I've got 2 GB RAM (actually 1.9, since part of it is used for video) and my swap file usage is zero, zip, zilch, nada, 0.0%

With 6 GB RAM you really don't need much swap, unless you will be running a server under heavy load or several concurrent resource-hungry applications.

The only reason to have a 6+ GB swap in your case would be in order to enable hibernation.  When you hibernate your system, Ubuntu saves the hibernation file on the swap partition.

---

### Post by JoshuaRL on 2008-06-04
The idea behind having separate / and /home  and swap partitions is to make the hard drive faster (just a tiny little bit) but really to save hard drive ware and tear.  

Depending how much RAM you have and what type of applications you use, the most used partition will be the swap.  The second most used partition by the OS is /.  That has all the system files and all the applications.  Then comes the /home directory with all your music and whatnot.  

By separating these, you save yourself some headaches in case of corruption or system failure.  Also, the hard drive read/write head makes less trips back and forth, and so lasts longer.

---

### Post by ubromtoo on 2008-06-04
Having a separate /home partition will make it easy to 

change from Hardy to the next release when it comes out, rather

than having to bother with "upgrading".

     imo, upgrading is far more trouble than it is worth. Better

to simply do a clean install, which will only involve the /

partition , and will leave the /home partition untouched.

---

### Post by JoshuaRL on 2008-06-04
That is a great point ubromtoo. I hadn't thought of that.

---

