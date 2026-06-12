---
title: "Hp dv2000 help with partition"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by liamr_spencer on 2008-10-26
Hi Guys,

Total Noob at this but hopefully someone can help me!
I have a hp dv2000 laptop and it is currently running Ubuntu. I want format the drive and set up two partitions so that i can run Ubuntu on one and vista on the other (don't hate me, but its necessary!). 

Does anybody know how I would go about that?

---

### Post by tompickles on 2008-10-26
Easiest and Safeest way as you have vista.

DEFRAG! DEFRAG DEFRAG! Can't emphasise that enough.

Then, in VISTA go to control Panel, and in there search for partitions. You will get a tool and it will allow you to shrink your partition for windows. and gives you some free space! I think if I remember rightly you just right click on the partition and select shrink and read a bit.


Then, boot from the Ubuntu CD and look at your partitioning and ensure that your NTFS partition is NOT formatted, and that nothing is resized. In the install use Guided: Use free space.

Hope that makes sense.....

---

### Post by liamr_spencer on 2008-10-26
sorry i prob didnt make myself clear. machine is running ubuntu completely without any partitions and i need to install vista on a partition which i need to create. can that be done?

thanks for the reply!

---

### Post by tompickles on 2008-10-29
You are doing this the *bad* way around! Linux plays happy if you install windows first, then linux, and the GRUB over the top of your mbr. I would seriously reccomend, unless you have tons of apps/configuartion/data on ubuntu, to start over... install vista, leaving a partition for ubuntu, then install ubuntu after. Maybe others will have better ideas.... but generally the advice ive heard is windows and then linux for an easier ride.

---

### Post by skintythe1andonly on 2008-10-29
AS far as I know tompickles is right, Vista would have to be installed first as when you install it second the windows bootloader overwrites grub. I think windows always has to be in the first logical partition too.

I know its slightly annoying but i suggest backing up all your data...then wiping the whole thing and putting Vista on it. Defrag and then you can use the windows partitioner or Gparted on the ubuntu live CD to resize. You can then install Ubuntu onto the sapce you have freed up. I know a clean install isnt ideal but at least you can do it now with Intrepid

---

### Post by tompickles on 2008-10-29
FYI vista no longer has to be in the first partition - this is a *new* feature of it, but yeh, i think the easiest in the long term is to start over im afraid.

---

