---
title: "Raw partition - dual boot Vista/Linux"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by supersickie on 2008-05-21
I had to wipe my laptop recently and - with Ubuntu in mind - I created a raw partition upon loading Vista back onto my machine.  My question is concerning the partition section of the Linux install.  Most of the tutorials I have found only guide the user through creating the partition/swap files within Linux.  I would very much appreciate any guidance concerning the Linux install since I have a partition ready to go.  

While I might sound overly cautious, I'm just terrified of accidentally wiping my hard drive (Vista install) and I'm really looking forward to learning Linux.  Just want to make sure I get off on the right foot.  Thanks in advance.

---

### Post by shifty_powers on 2008-05-21
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

will give you some guidance.

if you tell the installer to use the largest contiguous free spac on the drive, it should do it for you.....

---

### Post by supersickie on 2008-05-21
Thanks for those links.  Will Linux detect my raw partition as being the largest contiguous space even though the drive's already been partitioned?  I'm just wondering if I need to point the install to the other "drive".

---

### Post by shifty_powers on 2008-05-21
well yes it should, but you can use the manual option.

it will be obvious which is the raw space.

i usually set up / (i.e. root) as 5-10gig, /boot as 100meg, a swap partition of approx 1-4 gig, (depending on how much ram you have, usual advice is twice your ram), and a /home for the rest...

---

### Post by bilbo.san on 2008-05-21
I would suggest to choose manual installation during the LIVE CD install process, then create a 10 gb partition (ext3) for "\" about 15 GB for "\home" and perhaps 1GB for SWAP memory... that is what I did and worked just fine... OF COURSE you have to have a NTFS partition for Windows, which should not be touched.

Good luck.
b.

---

### Post by phr0ze on 2008-05-21
If you created the other partition with windows you will probably have to delete it. If you just created the windows partition and left the rest of the space alone, just choose the option you mentioned in the auto install. I don't recommend the manual partitioning unless you know what linux needs. Such as swap.

---

### Post by supersickie on 2008-05-21
I created the partition when first installing Vista so it's not even formatted yet.  Should I still have to delete it?  I created it with Ubuntu in mind in hopes of avoiding partitioning problems later.

---

### Post by melrom on 2008-05-21
> **supersickie said:**
> I created the partition when first installing Vista so it's not even formatted yet.  Should I still have to delete it?  I created it with Ubuntu in mind in hopes of avoiding partitioning problems later.


Yes but what did you use to partition? gparted? parted magic?

We're just trying to see if you used the Vista partitioner.

---

### Post by melrom on 2008-05-21
Also, if you have the space allocated and run the manual install option of the Ubuntu live CD, it will make it's own ext3 and swap.

---

### Post by melrom on 2008-05-21
> **melrom said:**
> Also, if you have the space allocated and run the manual install option of the Ubuntu live CD, it will make it's own ext3 and swap.

Just make sure it chooses the free space to install on. You can check this by verifying against the partition name of the free space as seen in gparted. The NTFS partition will be your Windows partition.

---

### Post by supersickie on 2008-05-21
> **melrom said:**
> Yes but what did you use to partition? gparted? parted magic?

We're just trying to see if you used the Vista partitioner.

I created the partition _while_ I was installing Vista, not after Vista was installed.  In other words, I set up a partition separate from what I was going to use for my Vista install.  Thanks for making me clarify; I'm all about getting this right.

---

### Post by supersickie on 2008-05-21
Any other advice concerning a dual boot in this situation?  It sounds like I should use the contintuous space option with hopes that it finds my unformatted partition.

---

### Post by melrom on 2008-05-21
If you do this and are very worried about it writing over the Windows parition, open up a terminal [assuming you're using the live cd] and type gparted. Just make sure that the name of the partition that the installer wants to install on does not match the name of the NTFS partition.

---

### Post by supersickie on 2008-05-21
I'll give it a go tonight.  Thanks for all of your help.

---

