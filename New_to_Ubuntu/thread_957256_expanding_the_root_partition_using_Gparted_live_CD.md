---
title: "expanding the root partition using Gparted live CD"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-10-24
my ubuntu 8.04 root partition is about 20 GB,and next to it lies 10 GB of free space.i tried using the Gparted live CD to merge the two to enlarge the root partition to 30 GB.but,there wasn't any option for expanding or growing the ext 3 root partition.how do i use the live CD then to do this?
thanks in advance.

---

### Post by bumanie on 2008-10-24
Whatever have you got in your / partition? 10gb should be ample space. I have a new installation of intrepid ibex beta and its / is only 2.7gb (Haven't installed much yet). However to increase the partition size, boot with ubuntu live cd > sudo apt-get install gpartedThen go to System --> Administration --> Partition editor. Right click on the partition you want to alter - it should be self-evident from there what to do.

Oops see you will use gparted live cd - basically boot with it and then do - Right click on the partition you want to alter - it should be self-evident from there what to do ie you can use sliders to increas the size of the partition and choose to have no free space between partitions.

---

### Post by quirks on 2008-10-24
@bumanie: Isn't GParted installed on the live CD by default?

@stonecoldjha: I believe, the reason why the resize/move button is disabled is because there are other partitions right next to the root partition, which you want to resize. You must delete/shrink the adjacent partitions to make space for your root partition.

If that does not work, run this command - it is helpful for us to know about your partition layout:

```
sudo fdisk -l
```

---

### Post by stonecoldjha on 2008-10-24
yeah,i want to know as to how i do it,after having loaded the graphic interface of the Gparted live CD.i mean i did not find anything that could help me expand it.

---

### Post by quirks on 2008-10-24
Right click the partition you want to resize and choose Resize/Move, as in this screenshot:

[http://apcmag.com/system/files/images/ubuntu_vista_02.article-width.jpg](http://apcmag.com/system/files/images/ubuntu_vista_02.article-width.jpg)

But beware: if you do not quite know what you are doing, you can delete all your data! So better ask, if you need any further help.

---

### Post by louieb on 2008-10-24
Does GParted say its unallocated?  Is it to the right or left of the root partition?  Look carefully:

[LIST]
[*]Is you root a primary partition and  the unallocated space inside an extended partition?
[*]Or vise versa is the root partition a logical partition and the unallocated space outside the extended partition?
[/LIST]

Probably  one or the other.  if so you'll need to resize the extended partition 1st.  Once you understand how primary, extended and logical partitions work it will be easy to expand the partition. 
  
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") 

And if you care about your data please backup your data 1st.

---

### Post by Duck2006 on 2008-10-24
This is from parted magic web site witch uses gparted.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)

---

### Post by stonecoldjha on 2008-10-24
the outcome of the command sudo fdisk -l yielded the following output:

[B]sonu@sonu-desktop:~$ sudo fdisk -l
[sudo] password for sonu: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb91eb91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       18172   115250310    f  W95 Ext'd (LBA)
/dev/sda3           18173       19457    10321762+  83  Linux
/dev/sda5            3825        7648    30716248+   7  HPFS/NTFS
/dev/sda6            7649       11472    30716248+   7  HPFS/NTFS
/dev/sda7           11473       15679    33792696    7  HPFS/NTFS
/dev/sda8           15680       15740      489951   82  Linux swap / Solaris
/dev/sda9           15741       18172    19535008+  83  Linux
sonu@sonu-desktop:~$ 
[/B]

---

### Post by quirks on 2008-10-24
Thank you for the output of fdisk. As I thought, there is another partition next to the partition you want to enlarge. According to fdisk, there is another Linux partition (/dev/sda3) next to the partition in question. In addition to that, the partition is inside an extended partition. As louieb correctly pointed out, you must enlarge the embracing extended partition before you can enlarge your 20GB Linux partition. Here is what you have to do:

WARNING: ONLY PERFORM THE STEPS BELOW IF YOU KNOW WHAT YOU ARE DOING. MAKE SURE THAT /dev/sda9 ACTUALLY IS YOUR LINUX ROOT PARTITION. AND MAKE PARTICULARLY SURE THAT THERE IS NO IMPORTANT DATA ON /dev/sda3.

1. Delete /dev/sda3 (the supposedly free space). MAKE SURE THERE IS NO IMPORTANT DATA ON IT ANYMORE!!!! EVERYTHING ON IT WILL BE LOST!!!!
2. Resize /dev/sda2 to the end of your hard disk, i.e. add the 10GB gained in step 1.
3. Resize /dev/sda9 to the new size of the extended partition (/dev/sda2).

If you have any further questions, just ask. If you are unsure what to do, better ask before you accidentally break something.

---

### Post by stonecoldjha on 2008-10-24
the attached screenshot was taken after i deleted the 10 GB partition.what do i do now?

---

### Post by jerome1232 on 2008-10-24
Now you will need to extend /dev/sda2 to the end of the disk, then you can extend your root partition.

before you proceed though I have a doubt as to whether that can be done without deleting the logical partitions inside /dev/sda2...

Can you extend an extended partition without wiping out the enclosed logical partitions? I've always just made 4 primary partions the last one being an extended partition that goes to the end of my drive.

---

### Post by Duck2006 on 2008-10-24
It can be done but it takes a lot of time.

---

### Post by louieb on 2008-10-24
> **jerome1232 said:**
> Now you will need to extend /dev/sda2 to the end of the disk, then you can extend your root partition.

+1 Don't have to delete a thing Just grow sda2 to end of disk. then the do the same to sda9. Should go pretty fast. 

(Growing to the right get done pretty quickly. Its when you grow to the left that takes a lot more time).

---

### Post by Duck2006 on 2008-10-24
> when you grow to the left that takes a lot more time

Sure does take a bit of time.

---

### Post by tlivingd on 2008-10-24
Don't mean to Hijack....

Is Gparted the best way to enlarge the NTFS of Vista?  

when putting Ubuntu on and after the bloat of SP1 my windows partition is too small.  when I run Gparted, I have a yield sign on the ntfs partition.

Thanks,

EDIT:  if it's not what is?

---

### Post by quirks on 2008-10-25
@tlivingd:

I am not quite sure, but I believe the warning symbol is not normal. As far as I can remember, this only appears, when the routine file system check returned an error (right-click the partition and click Information/Details; the report should show the errors if applicable). If the file system is corrupt, you should definitely have it checked and corrected by Vista before you modify it. A normal reboot into Vista should do it. Vista ought to detect the error during boot and automatically run autochk.

Apart from that, I have already resized NTFS numerous times using GParted (also with Vista) and it never broke anything.

---

