---
title: "Cannot access part of my memory!"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by dep0 on 2011-11-19
Hi, i used to have xubuntu and ubunutu installed on my pc (dual boot). I have just erased xubuntu using g-parted and i cannot access the memory that xubuntu were saved (again using g-parted).
Is there anything i could do.
I am just using half of my computer's memory right now and that's quite annoying.
HELP is needed!

---

### Post by haqking on 2011-11-19
> **dep0 said:**
> Hi, i used to have xubuntu and ubunutu installed on my pc (dual boot). I have just erased xubuntu using g-parted and i cannot access the memory that xubuntu were saved (again using g-parted).
Is there anything i could do.
I am just using half of my computer's memory right now and that's quite annoying.
HELP is needed!

I think you are confusing memory with hard drive space ?

Do you mean you removed xubuntu from your hard drive and now you cannot access that space ?

Gparted cannot see it you mean ?

HDD space is different to memory

---

### Post by dep0 on 2011-11-19
Oups! Sorry that is what i meant. I can access ubuntu of course but g-parted shows me a large not available space.
So, yes i cannot access the space of ex-xubuntu on my hard drive. 
Anything i could do?

---

### Post by haqking on 2011-11-19
> **dep0 said:**
> Oups! Sorry that is what i meant. I can access ubuntu of course but g-parted shows me a large not available space.
So, yes i cannot access the space of ex-xubuntu on my hard drive. 
Anything i could do?

when you say cant access it do you mean in gparted or within ubuntu ?

can you show us a screen dump of what you mean or your gparted layout then instead of guessing at something i can probably help more if i can see what you mean.

Cheers

---

### Post by dep0 on 2011-11-19
This is what i am getting when i run the gparted.
The grey space is not available.
I cannot access it in gparted. I have space left for ubuntu of course but it's just the half hard drive of my computer.
I have also read that in order to resize a partition in have to unmount it. That i cannot do probably cause i am in ubuntu when trying to unmount the partition that has ubuntu in it.
I am from greece so my english are not really good.
Excuse me.

---

### Post by plucky on 2011-11-19
> **dep0 said:**
> This is what i am getting when i run the gparted.
The grey space is not available.
I cannot access it in gparted. I have space left for ubuntu of course but it's just the half hard drive of my computer.
I have also read that in order to resize a partition in have to unmount it. That i cannot do probably cause i am in ubuntu when trying to unmount the partition that has ubuntu in it.
I am from greece so my english are not really good.
Excuse me.

Turn off swap on /dev/sda5 as it won't let you manipulate mounted partitions.

You should also be doing this from the Live CD.

What do you want to do with the space?

Good Luck

---

### Post by rng on 2011-11-19
Right click on 140 GiB empty space and choose 'New' from menu. Then create a new partition- ntfs/fat32/ext4/ext3- any format- and it should be available to ubuntu.

---

### Post by dep0 on 2011-11-19
OK. Done it! thank you all.

---

### Post by haqking on 2011-11-19
> **dep0 said:**
> OK. Done it! thank you all.

ha sorry i didnt get back earlier.

Looks like you got it sorted though.

Cool.

Cheers

---

### Post by dep0 on 2011-11-19
ha ha! No problem! thanks for the interest anyway.

---

