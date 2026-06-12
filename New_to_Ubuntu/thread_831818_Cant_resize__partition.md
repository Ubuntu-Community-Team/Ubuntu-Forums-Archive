---
title: "Cant resize / partition"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by darkline on 2008-06-17
I have tried expanding my / partition by booting into the live cd and expanding it (original setup in attachment). 

It hits an error when copying the blocks, all gparted says is an error has occurred, please look at the details.

details are here::-

```
GParted 0.3.3

Libparted 1.7.1

Grow /dev/sdb4 from 22.44 GiB to 47.95 GiB  07:10    ( ERROR )
     	
calibrate /dev/sdb4  00:00    ( SUCCES )
     	
path: /dev/sdb4
start: 108743985
end: 155798369
size: 47054385 (22.44 GiB)
calculate new size and position of /dev/sdb4  00:00    ( SUCCES )
     	
requested start: 55247535
requested end: 155798369
requested size: 100550835 (47.95 GiB)
new start: 55247535
new end: 155798369
new size: 100550835 (47.95 GiB)
check filesystem on /dev/sdb4 for errors and (if possible) fix them  02:07    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb4
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

177504 inodes used (6.02%)
7344 non-contiguous inodes (4.1%)
# of inodes with ind/dind/tind blocks: 10668/164/1
4525621 blocks used (76.94%)
0 bad blocks
2 large files

138992 regular files
19004 directories
132 character device files
26 block device files
2 fifos
571 links
19309 symbolic links (17952 fast symbolic links)
30 sockets
--------
178066 files
e2fsck 1.40.2 (12-Jul-2007)
move partition to the left  00:01    ( SUCCES )
     	
old start: 108743985
old end: 155798369
old size: 47054385 (22.44 GiB)
new start: 55247535
new end: 102301919
new size: 47054385 (22.44 GiB)
move filesystem to the left  05:02    ( ERROR )
     	
using internal algorithm
copy 47054385 sectors
finding optimal blocksize
     	
copy 32768 sectors using a blocksize of 64 sectors  00:04    ( SUCCES )
     	
32768 of 32768 copied
4.03808 seconds    ( ERROR )
copy 32768 sectors using a blocksize of 128 sectors  00:03    ( SUCCES )
     	
32768 of 32768 copied
3.82364 seconds    ( ERROR )
copy 32768 sectors using a blocksize of 256 sectors  00:04    ( SUCCES )
     	
32768 of 32768 copied
3.4795 seconds    ( ERROR )
copy 32768 sectors using a blocksize of 512 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
2.39434 seconds    ( ERROR )
copy 32768 sectors using a blocksize of 1024 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
1.82361 seconds    ( ERROR )
copy 32768 sectors using a blocksize of 2048 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
1.10583 seconds    ( ERROR )
copy 32768 sectors using a blocksize of 4096 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
0.903689 seconds    ( ERROR )
copy 32768 sectors using a blocksize of 8192 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
0.846465 seconds    ( ERROR )
copy 32768 sectors using a blocksize of 16384 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
0.763721 seconds    ( ERROR )
optimal blocksize is 16384 sectors (8.00 MiB)
copy 46759473 sectors using a blocksize of 16384 sectors  04:43    ( ERROR )
     	
8535601 of 46759473 copied
Error while reading block at sector 117574498
8830513 sectors copied
rollback last change to the partitiontable  00:00    ( SUCCES )
     	
move partition to the right  00:00    ( SUCCES )
     	
old start: 55247535
old end: 102301919
old size: 47054385 (22.44 GiB)
new start: 108743985
new end: 155798369
new size: 47054385 (22.44 GiB)
libparted messages    ( INFO )
     	
Input/output error during read on /dev/sdb

========================================

```

any way i can get this fixed and expand the partition?

i am running hardy, but the live cd is from gutsy.

ty

---

### Post by Yuki_Nagato on 2008-06-19
Gutsy's version that you are using seems to be version 0.3.3.  GParted has reached release 0.3.7, and the one included on the Hardy LiveCD is 0.3.5-1.  Perhaps you can boot to the LiveCD, and then update GParted, and then run it.

The alternative is to download GParted and create a LiveCD out of the latest version.

---

### Post by tysonh on 2008-06-19
I'm no partitioning pro but it might be because you have empty space in between your 2 main partitions.  I'm not sure if when you try to grow a partition it grows to right or not or if it will grow it in any direction.

You might have to delete your ext3 partition and move it to the left in the empty space.

---

### Post by bumanie on 2008-06-19
You should be able to slide the /dev/sdb4 partition to the left and then extend it to the right. You can't (from memory) extend a partition to the left, but you can slide/move it to left. Be aware that as the aprtition has a filesytem on it, this process could take a number of hours.

---

### Post by darkline on 2008-06-20
hmmm still doesnt seem to work, i guess ill just reinstall ubuntu, havent had it for long anyway.

Thanks anyway

---

### Post by Duck2006 on 2008-06-20
Or you can try parted magic.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Has some good documents as to how to use.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Documents](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Documents)

---

### Post by Dutch70 on 2008-06-20
> **bumanie said:**
> You should be able to slide the /dev/sdb4 partition to the left and then extend it to the right. You can't (from memory) extend a partition to the left, but you can slide/move it to left. Be aware that as the aprtition has a filesytem on it, this process could take a number of hours.

+1, if you are going to reinstall anyway.You can reinstall it to your unallocated space, and then grow it to the right, easily!

---

### Post by Cebonet on 2008-06-20
make sure everything is unmounted, and swapoff that swap part

---

### Post by darkline on 2008-06-21
I have done a reinstall using all the space i wanted so alls good now:)


just have to remeber what i had installed and tweaked. lol

thanks anyway

---

