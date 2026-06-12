---
title: "HALP! Partitioning!"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Ikith on 2008-05-02
I'm having a lot of trouble. I have 2 windows partitions and I want to add linux to my system. I have a 500 gig hard drive but I only want to use 20 gigs out of it but of course there are only these 3 options:

Guided resize SCSI3(0,0,0), Partition 1 (sda) and use free space. (I dont want to do this since this is a windows partition)
Guided Use Entire Disk (I want to keep my windows so this is out)
Guided use the largest continuous free space (I don't want to do this either because thats 300g)
Manual (I don't know how to use this so I'm seeking help)

How would I go about giving ubuntu 20 g of space without messing with my windows partitions?

---

### Post by TeoBigusGeekus on 2008-05-02
You have to go to manual... 
It's not that hard. You just choose the volume on which you want Ubuntu installed, create a partition of 19gb (format ext3 - mount point /), which will be your root partition, and another partition of 1gb (swap).
You can of course set a different partition for your home folder (highly recommended): I' d say 10gb (ext3-/), that's your root, 9gb (ext3-/home), that'll be your home folder, and 1gb for swap.

---

### Post by Oldsoldier2003 on 2008-05-02
> **Ikith said:**
> I'm having a lot of trouble. I have 2 windows partitions and I want to add linux to my system. I have a 500 gig hard drive but I only want to use 20 gigs out of it but of course there are only these 3 options:

Guided resize SCSI3(0,0,0), Partition 1 (sda) and use free space. (I dont want to do this since this is a windows partition)
Guided Use Entire Disk (I want to keep my windows so this is out)
Guided use the largest continuous free space (I don't want to do this either because thats 300g)
Manual (I don't know how to use this so I'm seeking help)

How would I go about giving ubuntu 20 g of space without messing with my windows partitions?

create a 20G partition in the free space using gparted. you'll also need a swap partition typically 1mb max unless you plan on using suspend in which case you need to at least match your installed ram in size.

or you could just have the installer do all the partitioning as stated in the post above.

---

### Post by billgoldberg on 2008-05-02
I'll guide you through the steps

1. Partition your harddrive so there is a 20gb partition for ubuntu to use.

Also make sure there is a 2 gb partition available for swap.

(you could use the gparted live cd for that, I think that gparted is available from the ubuntu live cd, not sure)

Use google if you don't know how use gparted (it's pretty straight forward)

2. Install ubuntu, go to manual and look for the 20 gb partition you created.

I think you will need to edit the parttion. Choose the format the drive to "ext3" and assign the mouse point (could be a different name) "/" to it.

Then do the same for the 2 gb swap partition but instead of "/" choose "swap" from the list.

That's it.

---

### Post by Ikith on 2008-05-02
Would say creating a NTFS partition after a 50g unallocated allow me to hit the 3rd option since everything else is being used? Or would that cause it to create an extended.

Edit: Nevermind. It goes to extended!

Thank you billgoldberg, teo, and old

---

### Post by phoenix_abhi on 2008-05-02
If U have 2 win dows partition namely c and d correct. What is the alocation size of them

Here I will mention abou partitioning in simple way

1. U can allocate a windows partition ( Before that u have 2 make one according to desired size for linux). Suppose u made 3 partitions ie c - 240, d 240 e 20. Go to manage in my computer rt click menu. select diskmanagement delete the 20 gb partiton (e). Now restart the pc loading live cd and go to install. Select manual. It will show all three partitions. here u can easily find the partiton by size diffrence. select the 20 gb one and allocate 2 X gb of ur ram as Swap. Select rest as ext 3 and root (/). Now start the installation.

---

