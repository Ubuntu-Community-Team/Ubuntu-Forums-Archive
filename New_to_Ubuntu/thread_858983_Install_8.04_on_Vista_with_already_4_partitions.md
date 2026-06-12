---
title: "Install 8.04 on Vista with already 4 partitions"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by pjvandehaar on 2008-07-14
Ive already dual-booted Ubuntu with xp, but now I'm trying it on Vista. For some reason it already has 4 partitions, though. I'm not sure if I can delete the first and last or put them in an extended partition. And I could put Ubuntu in an extended partition with its swap partition, right? Also, am I right that having more free space increases my chance of not losing everything?

---

### Post by pjvandehaar on 2008-07-14
Also, this is a Dell inspiron 1721, if that helps.

---

### Post by CheeseEatingBulldog on 2008-07-14
I would be interested in a sollution for this as well, my old man has a Vaio which has 4 partitions due to one restore partition of the factory default. Tried to dual boot, but he was scared of losing / breaking his current install / restore partition.

---

### Post by spydon on 2008-07-14
You need to make 3 primary partitions and an extended partition that you can make more partitions in.
What do you have the 2.5gb and 70mb partitions for?

You could just shrink your sda3 and give the extended partion (sda5) more space and then make the Ubuntu partition and the swap partition in the extended partition like you said.

---

### Post by pjvandehaar on 2008-07-14
I probably have less of an idea what those are than you do. I wouldn't think they could be anything important. possibly vista's version of swap, though.
Even if extended partitions could fix the problem, i still need to do something with one of the small partitions while making the extended one.

---

### Post by spydon on 2008-07-14
No, because you already have an extended partition. :)
Vista doesn't use a swap partition it uses a swap file instead.

---

### Post by overdrank on 2008-07-14
Hi Yes  you have a extended partition but the space available is outside of that partition. I believe you will have to delete the extended partition and then resize the windows partition and then recreate the extended partition for the install of Ubuntu.

---

### Post by kansasnoob on 2008-07-14
OK resize Vista with Vista's own tools only. Read page 2 of this tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

When you are done have a look again with the Gparted Live CD (or Gparted from you Ubuntu Live CD, and you should see a smaller sda3.

If so you should then be able to resize sda4 (regaining the space freed up by shrinking Vista). Then the unallocated space will be larger, that's where you'll want Ubuntu and it's swap.

I never like to "shrink" a partition to less than 125% of it's "used" size, 150% is even better. Lets say 100gb of that 220gb partition is "used". I would not shrink it smaller than 125gb to 150gb.

BTW Ubuntu can live well on as little as 10gb, but I'd suggest more.

---

### Post by kansasnoob on 2008-07-14
Oh, and don't delete any of those partitions, you don't need to.

After you've installed Ubuntu and have everything working properly you'll be able to read any FAT or NTFS partitions/files!

---

### Post by overdrank on 2008-07-14
> **kansasnoob said:**
> 
If so you should then be able to resize sda4 (regaining the space freed up by shrinking Vista). Then the unallocated space will be larger, that's where you'll want Ubuntu and it's swap.



The op will not be able to install ubuntu and the swap on that partition be cause there are three partitions and ubuntu and swap will make five. Four is the total amount allowed unless the partition is extended. That is the reason for my post.

---

### Post by louieb on 2008-07-14
> **kansasnoob said:**
> ...When you are done have a look again with the Gparted Live CD (or Gparted from you Ubuntu Live CD, and you should see a smaller sda3...If so you should then be able to resize sda4...

+1
 After shrinking VISTA w/Vista's tools. Fire up GParted.
1st grow extended partition sda4 to the left to fill up all the unallocated space. (the space will still show as unallocated but now its inside the extended partition)
2nd now you can add logical partitions for / (root), swap and /home if you want.  (:) If I remember right a sata drive does limit you to 15 logical partitions).

kansasbob is right on with his advise.

---

### Post by pjvandehaar on 2008-07-24
I was following all your instructions, but after defragging i could only reduce the vista partition by 641 mb. I have a 220gb hard drive, and only using 120gbs. any help?

---

### Post by spydon on 2008-07-25
Could you see if there was any unmovable files in the end of the partition when you defragged?

---

