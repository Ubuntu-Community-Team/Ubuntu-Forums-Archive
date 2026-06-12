---
title: "Partition"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by shewy on 2008-06-16
So im fairly new to this and i jsut got my live cd working, i have a 500g external hard drive like about 150gs used that i need to keep on there, i need to partition it so that i can have a partition for ubuntu, somehow i never learned how to make partition, iv never had to before, so how can i make one without loosing data off the drive if possible,

thanks, Richard

---

### Post by rraj.be on 2008-06-16
Its not a big issue.

Just use Gparted to partition .

I think this will help you a lot.

```
[www.howtoforge.com/partitioning_with_gparted]("www.howtoforge.com/partitioning_with_gparted")
```

```
[http://www.hermann-uwe.de/blog/resizing-ext3-partitions-with-parted]("http://www.hermann-uwe.de/blog/resizing-ext3-partitions-with-parted")
```

---

### Post by forestpixie on 2008-06-16
There is a partition editor on the livecd - system - admin menu.

Open that go to your drive in the dropdown menu - select the existing partition and resize it. 

Then you will have some unallocated space which the installer will recognise as such.

---

### Post by Raccoon1400 on 2008-06-16
> **forestpixie said:**
> There is a partition editor on the livecd - system - admin menu.

Open that go to your drive in the dropdown menu - select the existing partition and resize it. 

Then you will have some unallocated space which the installer will recognise as such.

that's gparted.
There is also a gparted live  cd.

---

### Post by forestpixie on 2008-06-16
> **Raccoon1400 said:**
> that's gparted.
There is also a gparted live  cd.

Yes I know - but last time I looked at it it was called Partition Editor so didn't want to confuse the issue. There is also partedmagic which I prefer :)

---

### Post by wolfen69 on 2008-06-16
+1 for partedmagic. and you are automatically root with it.

---

### Post by housam on 2008-06-16
Backup your data before resizing. just in case.

---

### Post by shewy on 2008-06-16
sooo i got the partition made now im trying to install to it and it says that there is no root file or something like that, i think i was reading something about it needing to be fat32, or i could be completly missled and that not be the problem at all,

thanks, richard

---

### Post by rraj.be on 2008-06-16
in the screen which shows you patition types you should select 

mount point as 

```
/
```

then proceed

---

### Post by forestpixie on 2008-06-16
You have to do 'edit partition' then you'll get a new window - in that new window is a drop down mountpoint menu - that is where you tell it to set mountpoints

for the root partition use /
for home use /home

if you wan tthe home to be not reformatted don't tick the format box

---

### Post by shewy on 2008-06-16
so lets start off at square one, as of right now my drive has no partitions and is 500g, i want a 250g partition one ntfs for my windows stuff and then the other for ubuntu, how would i go about doing this?

---

### Post by forestpixie on 2008-06-16
Depending on ram - change swap to suit - 1.5xRAM for swap

make a primary partition - format to ntfs

make an extended partition in the remaining space

in the extended partition make

logical partition 10Gb
logical partition 238Gb
logical partition 2Gb

---

### Post by shewy on 2008-06-16
what file systems should i use?

---

### Post by forestpixie on 2008-06-16
I use ext3 myself but there are other linux types about which I know little

---

### Post by shewy on 2008-06-16
so i am using the live cd under system and gparted to partition this after i do this how will i install to these partions?

---

### Post by forestpixie on 2008-06-16
I thought was what you were talking about previously - when you get to the partition part of the installation, choose manual and you will get a list of your new partitions - then you can 

>  'edit partition' then you'll get a new window - in that new window is a drop down mountpoint menu - that is where you tell it to set mountpoints

for the root partition use /
for home use /home

swap will take care of itself.

Once you've set everyting how you think - it doesn't actually make any changes until you hit next/go or whatever it is.

If you want to make sure post a screenshot, anyone seeing it will give you an answer I'm sure.

---

