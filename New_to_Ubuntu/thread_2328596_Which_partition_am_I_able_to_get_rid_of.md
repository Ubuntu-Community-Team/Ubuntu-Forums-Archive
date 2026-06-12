---
title: "Which partition am I able to get rid of?"
date: 2016-06-22
forum: New to Ubuntu
---

### Post by myriame on 2016-06-22
Hi, I'm very new to this and don't know all the technical terms, so bear with me please :D

I'm attempting to dual boot my laptop and I'm trying to install Ubuntu alongside (I have Windows 7), but I got to the point where I create a new partition through the free space and make it primary, using it as 'swap area', the free space goes to unusable and I can't do anything with that:
[ATTACH=CONFIG]269719[/ATTACH]

I looked around and found that it's probably because I can't have more than 4 partitions on my laptop (Toshiba) so I looked up what each partition is used for and this is what I find in the GParted Partition Editor:
[ATTACH=CONFIG]269721[/ATTACH]

Can anyone suggest what I can do or which I should be able to delete or replace without ruining anything?

Thanks.
(sorry if this is in the wrong section)

---

### Post by Manuel_Olivier on 2016-06-22
Hello Myriame

Just to check out, do you mean you wish to use both Windows and Linux so you don't want to delete anything on your previous OS? Or do you wish to move completely to Ubuntu and keep Windows in case of emergency?
I'm asking to check if you plan to free disk space in order to install Linux later or not

Manuel

---

### Post by myriame on 2016-06-22
Thanks for replying.

I plan on only using Ubuntu and keeping Windows just in case.

If I'll have to get rid of Windows, I don't mind.

---

### Post by Manuel_Olivier on 2016-06-22
Okay, so I guess you didn't format your HD yet? This is an important step before installing Linux, it takes less space on your disk so you can edit any partition while installing Ubuntu (or any other flavour you want...)

I would advise you to take a look at a tutorial, for instance:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

I hope this helps you

Manuel

---

### Post by deadflowr on 2016-06-22
Seems to be MBR (over the newer GPT) partitioned.
So, delete that swap partition and make an extended partition with that space.
then make a partition with that 18/19GB that shows as unusable, and then make the rest for swap.

MBR partitioning is limited to only 4 primary partitions, so when you made the swap partition, it left all that extra space unusable, since it cannot add anymore partitions for the space.
Luckily, to expand the limit of partition, you can create a single primary partition as extended.
This is a container for what are known as logical partitions, of which you can add a multitude of.

(GPT partitions, which is newer, does away with the 4 primary partition limit.
But really moot to this thread.)


When you actually install Ubuntu, in the installer's section on where/ how to install it, use the last option on the page called "something else".

In this section, you highlight the partition you set up for the 18/19GB and click on the change button.

In this section you set the mount point (dropdown) to / (/ means root, or main filesystem)
and also set the filesystem type (dropdown); 
(best file system type for Ubuntu is the default ext4)
then click okay.

(If you set swap partition in g-parted, then no need to do anything about that here.)

Last thing to do will be to double check where the bootloader is installed.
On the something else main page in the bottom area is a small section for the bootloader installation placement.
Best option is to set that to /dev/sda (and only sda, not sda2 or sda1 or whatever, simply /dev/sda)

When the partitions are set click on the install button.
Follow the rest of the instructions that come and Ubuntu will be installed.

Hope it helps.
Or makes sense.

---

### Post by myriame on 2016-06-22
> **deadflowr said:**
>  In this section you set the mount point (dropdown) to / (/ means root, or main filesystem)
and also set the filesystem type (dropdown); 
(best file system type for Ubuntu is the default ext4)
then click okay. 

Do I do this ^ to the free space?

I did choose to use "something else", and I can't 'change' the free  space, I can only create a new partition from it. When I create a new  partition the free space becomes "unsuable", and the new space, after  making it "use as:swap area" becomes "/dev/sda4 swap/" and I can change  that. 

> **deadflowr said:**
> 
So, delete that swap partition and make an extended partition with that space.
then make a partition with that 18/19GB that shows as unusable, and then make the rest for swap. 

I'm not given the option to make an extended partition of that space.
[ATTACH=CONFIG]269724[/ATTACH]

The only way I can make it extended is in GParted:
[ATTACH=CONFIG]269726[/ATTACH]
[ATTACH=CONFIG]269727[/ATTACH] Is this what you mean?

---

### Post by deadflowr on 2016-06-22
You can set it in the installation page.
Just set it as logical.
It'll make the extended partition for it.
Then set both the mountpoint and the filesystem type.
 
Note: You will need to shrink that partition a little to be able to create a swap partition.

It'll take moment to adjust itself when you click on OK.
But when it comes back, you should have a new entry for the partition you just set 
(with both the mountpoint showing (/) and filesystem type (ext4) and the size of course.)

You should also have a newer, smaller free space now. This should be for the swap.
Highlight that new free space click on change and it should automatically be set for a logical partition, and you can simply add the file system type linux-swap.
swap has no mount point so, that is all you need to do.

Does that make sense?

---

### Post by myriame on 2016-06-22
Yes it does!

It worked, thank you so much! :D:D

---

