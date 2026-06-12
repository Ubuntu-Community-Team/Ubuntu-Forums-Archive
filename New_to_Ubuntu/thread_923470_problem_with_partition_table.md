---
title: "problem with partition table"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by xieu90 on 2008-09-18
hi everyone
i used ubuntu 8.04
today i bough a new hdd (250 gb)and i had an old hdd 160gb
i just plug the new one into it, and there was not any jumper in the new one and i wanted to copy everything from the old one to the new one
in the old one there were 4 partition
20 GB for UBuntu
10 gb for xp
110-120 gb to store things like music ,video and so on
and 500 mb swap for ubuntu

after plug the new one i boot to live cd of ubuntu and created new partiton on the new hdd
there would be also 
20 gb for ubuntu 
10 gb for windows (when i made this partition i marked it as unused)
110 gb ext3 (sorry dont remember the name of this kind of partition ntfs for windows and e.... for ubuntu)
and 110 like the one above

and i installed ubuntu
after thatmy computer boot into the old ubuntu
and at the boot menu i didnt see anything new
but in the ubuntu i can see 2 new 110 gb partition but couldnt do anything

after taht i boot into xp cd and wanted to format one of 110 GB to ntfs so i can quickly finish the job 
there i saw only c:130GB
d:130 GB

it was bigger than those two 110 gb

but i was lazy and careless so i just deleted the d one
and pressed f3 to reboot
now

after restart my computer doesnt boot into ubuntu, the boot menu wouldnt appear either
i go back to live cd of ubuntu and see that the whole 160 gb old hdd is free place
there is some ubuntu on the 250 and it uses 130 gb partiton or i dont know how much it is.


now i let those 2 hdd in two different computer
the 160 in an old computer and the new one 250 is in my computer

i want to recover that 160 gb
how can i do that ?

and now i see that all 4 partition of 160 are merged into one partition.i tried something like gparted and it showed me a merged one. 

i havent format or rewrite that 160 so i hope there is some hope there.
help me !!!!!

---

### Post by jbrown96 on 2008-09-18
I can't really follow what you are saying. With both drives connected, could you post the output of ```
sudo fdisk -l
```

---

### Post by xieu90 on 2008-09-18
all i want now is the data from my 160 GB HDD

which had some partitions on it and those was somehow deleted. how can i recover the partition table and the data from it ?

---

### Post by jbrown96 on 2008-09-18
> **xieu90 said:**
> all i want now is the data from my 160 GB HDD

which had some partitions on it and those was somehow deleted. how can i recover the partition table and the data from it ?

You might try this from xopher on this [thread]("http://ubuntuforums.org/showthread.php?t=319096")

> Quote:
 TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting your Partition Table). Partition table recovery using TestDisk is really easy. 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
 
 and
 
Quote:
 PhotoRec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (Photo Recovery) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it'll work even if your media's filesystem is severely damaged or formatted. PhotoRec is safe to use, it will never attempt to write to the drive or memory support you are about to recover lost data from. 
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
 
 Now we need a quick guide how to use them as efficient as possible..
 
 EDIT:
 
 Both are available from the ubuntu repositories.

---

### Post by xieu90 on 2008-09-19
now i want to copy files from the broken hdd into the new one. how should i do it with testdisk in ubuntu ?

creat log or what exactly ?

---

### Post by jbrown96 on 2008-09-20
Sorry, I don't know anything about the software. I just ran a search and it looked promising.

---

