---
title: "[SOLVED] ERROR 22, cannot boot!"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by germanix on 2008-10-04
I do some dumb things at times, but this time I was just plain stupid. it all started yesterday when I treid to create a separate partition for my home file. I did manage to create the partition but must have made some mistake with the entry to the nano text file. (I was using the "How To" on [www.psycocats.net](www.psycocats.net)) The end of the story was Ubuntu could not find the Home file and I could not restart or quit. I cut the power and called it a day. I have a dual boot Ubuntu and Mint. This morning I booted into Mint and then did something realy stupid. I went into GParted, mounted the Ubuntu partitions and deleted them. I was meaning to re-install Ubuntu as my sole OS. I put in the live CD, hit restart, waiting for the PC to boot from the live CD. All I get is error 22 and cannot boot, neither from the live cd nor without it. I have no idea what to do next. This is what I would like:
Boot from the live cd, install Ubuntu as only OS, with a separate partition for Home. Currently I have 4 partitions on the drive. One each for Ubuntu/Mint OS and two large partition unused.
Anyone out there that could help?

---

### Post by shifty_powers on 2008-10-04
i would use the gparted live cd, assuming you hav already backed up any important data.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

make sure your bios is set to boot from cd BEFORE the hard drive

create the partitions you want and format them.

then boot from the ubunut livecd, use manual partitioning and mount the partitions as you want...

---

### Post by bumanie on 2008-10-04
I believe I answered your original question re this situation yesterday. I suggested that you format the whole drive and install ubuntu by choosing **manual** at the partitioning stage. At this point, I think that is your only option now. Make / 10gb; /home as large as you like; and swap 1-2gb. Use gparted, either from the live ubuntu cd or download gparted live cd to format the drive to ext3 before starting. This will get rid of mint as well as the extended partitions you had. With only three partitions there are no advantage to having an extended partition IMO - extended partitions on a main OS (other than swap) is limiting.

---

### Post by germanix on 2008-10-04
Sounds like a good idea presuming that the pc will boot from the GParted live cd. It wont boot with the Ubuntu live cd? Using the manual partitioning would be fine if I knew my way around, which I dont. The whole rolem started with me fiddling with the partitioning. With me it is realy a case of "fools rush in where angels fear to walk"
I keep making the dumbest mistakes.

---

### Post by germanix on 2008-10-04
I have booted with the Gparted live cd. I now have a screen that gives me thwe following options.
Select keymap from arch list
do not touch keymap (highlighted)
Keep kernel keymap
select keymap from list

<OK>    <cancell>

Which do I choose? (if this has something to do with the keyboard, I need the german keyboard)
I do not know how to choose/Make the selection between Ok or cancell?

---

### Post by bumanie on 2008-10-04
If your computer won't boot a live cd, that could be a problem, but there are other ways to go about installing ubuntu - won't confuse matters by discussing them as yet. Check your BIOS to ensure the computer is set to boot from cdrom as the first boot device. 
As far as jumping in to things - I think we all have done that at times, but at the end of the day, mucking things up makes one learn more than one ever can when everything always goes right. It can be frustrating, but it the end you will learn a lot!

---

### Post by shifty_powers on 2008-10-04
try pressing tab and then using the arrow keys.

just select keymap from list and use german keyboard layout...

---

### Post by germanix on 2008-10-04
OK I am now in Gparted. Currently it shows 0ne ext3 partition 10GiB, 0ne linux swap 6 GiB, two large partitions unallocated. How do I proceed?

---

### Post by shifty_powers on 2008-10-04
delete all the partitions.

this will create one large unallocated block.

then create the partitions you want.

i use four...

/ which is the root directory where you progs go. i usually give 20-30 gig for this.
/boot where your boot file go. i give 500meg for this, which is probably overkill
/home which is your home directory, and this is the rest minus swap
/swap which is the swap partition, twice your ram is fine.

all of them formatted for ext3.

then boot into the live cd, manual partitioning, then you set the mount pounts and don't format...

---

### Post by germanix on 2008-10-04
I do not seem to be able to delete the un-allocated blocks. I now have two large allocated blocks?
I tried to partition the way you suggested, but can only have max 4 ext3 primary drives. The fact that already have these two un-allocated complicates matters.
What is a ext2 partition used for? or which of the suggested partitions can I give either an ext 2 or a non primary allocation.

I now have the following situation:
sda1 14 GiB ext3 to be used as /root
sda3 8 GiB formatted as swap (cannot ger it any smaller)
sda 4 130Gib ext3
sda5 150GiB ext 3 planned as /Home

I was not able to combine the two large un-allocated blocks into one block. The situation now is somewhat unfortunate I think.I dont know what I would use sda4 for. seems like a waste of space? Any suggestions?

---

### Post by bumanie on 2008-10-04
Wonder whether the two unallocated partitions are in fact one unallocated partition with another within an extended partition (extended partition is surrounded by a blue coloured rectangle). You should be able to delete the extended partition and be left with one large unallocated partition. Then you can format it to ext3. Could you post a screenshot of your gparted GUI if there is not an extended partition.

---

### Post by germanix on 2008-10-04
I completed the partioning with Gparted then tried to boot from the Ubuntu live cd but the pc will not boot, still giving me error 22

---

### Post by shifty_powers on 2008-10-04
you are getting grub errors, which is very strange.

this what we do.

go and grab dban's nuke boot disk from:

[http://www.dban.org/](http://www.dban.org/)

burn the cd, boot and nuke the hard drive to buggery.

then boot from the ubuntu ccd, (you might want to download a new one and reburn it ata low speed, just to be safe), and install.

warning: this will all take some time....

---

### Post by germanix on 2008-10-04
Even after I have done the partitioning with Gparted live disk, the pc will not boot with the Ubuntu Live CD. I still get the error 22 message?

---

### Post by germanix on 2008-10-04
I do not know how I did it, but Ubuntu is now installing. I thank you all for the help.

---

### Post by shifty_powers on 2008-10-04
glad to help :D

---

