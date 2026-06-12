---
title: "[SOLVED] Question about partitioning for dual-boot"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by ROldford on 2008-11-06
I've recently gotten a Ubuntu install CD, and I'm interested in installing it on my laptop which also has Vista. I know I'll have to change the drive's partitions. Currently, my drive has 2 partitions, a small Recovery partition and a much larger Windows partition. These have not been changed since I got my computer.

According to what I've read, after defragging and backing up my files, I'll have to shrink my Windows partition and use the rest of the space for other partitions (I'm planning on 4: Shared Data, Ubuntu, /home, and swap).

However, the things I've read are unclear about what happens to the data on the Recovery and Windows partitions. Some seem to say that nothing will happen, while others say that those partitions will be wiped clean due to reformatting.

Can anyone tell me what will actually happen? I'd rather not lose access to Windows completely, and since I don't have the original disks, that seems like a real possibility. After all, I've got plenty more Spore to play. :)

One other question: Should I keep my Windows programs in the Windows partition, or can I move them to my Shared Data partition? Can Linux programs live there too, or should they stay "on their own side?" (I'm not worried about optimum read times or such things. I just want to know if it would work properly.)

Thanks!

---

### Post by tuxulin on 2008-11-06
what laptop do you have ?

if you have a partition with > data on the Recovery and Windows partitions i dont think by dual booting will damage those partitions.

the MBR is the part of the drive which is changed.
firstly back up all your partitions or better still use "ghost 8" to image
your drives.
then shrink your windows partition using "partition magic" then simply
install ubuntu. during the install it will ask how you want to set up your
drives choose "manual" next choose the newly created partition. ubuntu will 
then be installe to this partition. if you have 1gig over in RAM then a 
swap drive is not really needed unless of course your working methods 
requires it.

good luck, it will be OK :)
TUX

---

### Post by manishtech on 2008-11-06
> **ROldford said:**
> I've recently gotten a Ubuntu install CD, and I'm interested in installing it on my laptop which also has Vista. I know I'll have to change the drive's partitions. Currently, my drive has 2 partitions, a small Recovery partition and a much larger Windows partition. These have not been changed since I got my computer.
Dont worry about this. You just need to carve out new partition(s) from the exsiting Windows partition so that you can use it for Ubuntu.

> **ROldford said:**
>  According to what I've read, after defragging and backing up my files, I'll have to shrink my Windows partition and use the rest of the space for other partitions (I'm planning on 4: Shared Data, Ubuntu, /home, and swap).
You need to shrink the windows partition and make space for Ubuntu. I recommend to make 2 new partitions or 3 new if you want to have a dedicated /home.
What to do it to create one partition of size equal to / + swap + /home ,say 12GB.
When this is created, goto Ubuntu installation and when it asks for partition selection, choose Manual. Then delete this new partition and create 3 new partitions out of the free space created by deletion of partition.

> **ROldford said:**
>  However, the things I've read are unclear about what happens to the data on the Recovery and Windows partitions. Some seem to say that nothing will happen, while others say that those partitions will be wiped clean due to reformatting.
Your recovery partition will not be even touched, just resize the C: partition where Windows is installed.

If you are unable to shrink the partition using Vista's inbuilt partitioner, [refer to this guide]("http://devdjay.googlepages.com/VistaPartitionGuide.pdf")


> **ROldford said:**
>  Can anyone tell me what will actually happen? I'd rather not lose access to Windows completely, and since I don't have the original disks, that seems like a real possibility. After all, I've got plenty more Spore to play. :)
If you dont play with the rest two partitions, you wont land in trouble.

> **ROldford said:**
> One other question: Should I keep my Windows programs in the Windows partition, or can I move them to my Shared Data partition? Can Linux programs live there too, or should they stay "on their own side?" (I'm not worried about optimum read times or such things. I just want to know if it would work properly.)

Ubuntu can read Windows partitions and even display them. So you can use C: for shared data between both operating systems.
The sorry news is that Vista cant read Linux partitions

[COLOR=Red]**[Still unable to figure out why MS isnt adding the support]**[/COLOR] :(

Still having problems, report your problems ASAP

---

### Post by manishtech on 2008-11-06
> **tuxulin said:**
> 
then shrink your windows partition using "partition magic" then simply
install ubuntu.
Please Please! NO Partition Magic! Its a well known software which can simply screw up the filesystems badly. Its fine to use with XP but a big NO NO with Vista.
The reason is that Vista keep a Filesystem table with it apart from the disk volume information. Always resize/shrink Vista partitions with Vista's inbuilt partitioner or there are high chances that partitions may get screwed up.

---

### Post by Tom.Servo on 2008-11-06
> **manishtech said:**
> Please Please! NO Partition Magic! Its a well known software which can simply screw up the filesystems badly. Its fine to use with XP but a big NO NO with Vista.
The reason is that Vista keep a Filesystem table with it apart from the disk volume information. Always resize/shrink Vista partitions with Vista's inbuilt partitioner or there are high chances that partitions may get screwed up.

I agree with not using Partition Magic on Vista. The best method I have found is to simply boot with the gparted disk. Works 100% every time.

---

### Post by ROldford on 2008-11-06
Thanks for all your help. Being able to use the Windows partition in Vista should really help a lot. Once I figure out a good way to backup my drive without using a ton of DVDs I should be just fine. :)

---

