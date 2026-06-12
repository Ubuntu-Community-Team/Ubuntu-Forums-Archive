---
title: "[SOLVED] adding a partition long after install"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-27
i am looking to add a partition to Ubuntu

i found that i need some more space so i am going to use some free space i had kept for winblows to make a new partition..

i would like it to be   /usr/games/
 
i dont have a clue how to get it do auto magically mount everything
at start..

i dont even know how to add the partition into linux
im going to use a boot disk (hirens boot cd) to resize the old partition and create a new one for linux...

after that i am lost..
my google-fu is not giving me usable information

any hints?
tell me there is an easy way to permanently add the partition.
nutz

---

### Post by bwhite82 on 2008-05-27
There's a good tool called gparted that can accomplish this for you.

---

### Post by ZabiGG on 2008-05-27
And there's loads of basic information I fear you haven't read about your system... Click on the "Look here" link in my signature below for a list of useful basic documents.

Cheers,

Z.

---

### Post by nutpants on 2008-05-27
> **ZabiGG said:**
> And there's loads of basic information I fear you haven't read about your system... Click on the "Look here" link in my signature below for a list of useful basic documents.

Cheers,

Z.

your right there is a lot of info that i have to learn to work my way around linux and ubuntu. and i read as much as i can when i can. computers are not my life and i will never have to time to learn every command line option for linux like may of the most helpfull users here.

gparted has no option for setting a mount point for Ubuntu that i can find. so i keep looking how to add a new partition as a mount point with out having to read 5000 not useful pieces of information to find the one i need.

i know it has to do with ftab now the question is how to add it..

nutz

---

### Post by ZabiGG on 2008-05-27
Hi again ;)

The thing is, you won't be able to create a partition from an existing folder. You can only partition empty space.

You need to create a partition first, then move your folder to your new partition.

After that, you will need to modify your fstab file to automount your new partition.

EDIT: the info links I gave you can be used for help on a need-to-know basis and are presented by subject to help. Just bookmark it and use it as you need ;)

Hope this helps,

Z.

---

### Post by nutpants on 2008-05-27
ok it worked out..
i created a new partition (after resizing one i was not using as much) 

it was created as /dev/sda6   (which messed up my grub something bad but thats another story)

i created a new directory for it by running nautilus as sudo

i edited /etc/fstabs  to add something that looked something like this

# /dev/sda6
UUID=f53ad4f5-d674-0d11-a490-4x0x086x3x1x /usr/games	  ext3    relatime        0       2      
 
rebooted and its working fine..

im not real sure how it did it  but these are the steps i took to make it happen..

nutz

---

