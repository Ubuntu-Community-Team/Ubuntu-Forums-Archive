---
title: "Help to make a sh script to resize NTFS partitions"
date: 2010-09-01
forum: Programming Talk
---

### Post by marietto2008 on 2010-09-01
Can someone help me to make a shell script to resize automatically the NTFS partitions of my disk ? 

This is the partition table :

Disk /dev/sda : 320 GB

/dev/sda1 = boot,primary = 27 GB
/dev/sda2 = primary = 129 GB
/dev/sda3 = primary = 161 GB
Free space = = 3 GB

/dev/sda1 should be expanded to 1 GB
/dev/sda2 should be reduced of 1 GB

This is in detail what I need to script :

ntfsresize -f -s 128G /dev/sda2

fdisk /dev/sda
p

/dev/sda1 = start 1 end 3284 blocks 26378698
/dev/sda2 = start 3285 end 19000 blocks 126238770
/dev/sda3 = start 19001 end 38913 blocks 155942955 

d
2
n
p
2
first cylinder (3285-19000,default = 3285) : 3785 = (default + 1 GB cylinders ; the number 3785 is only an example)
last cylinder,+cylinder or +size(K,M,G) (3785-19000,default 19000): 19000
t
2
7
w

fdisk /dev/sda
p

/dev/sda1 = start 1 end 3284 blocks 26378698

(3285-3784) = free space

/dev/sda2 = start 3785 end 19000 blocks 126238770
/dev/sda3 = start 19001 end 38913 blocks 155942955 

d
1
n
p
1
first cylinder (1-3785,default = 1) : 1
last cylinder,+cylinder or +size(K,M,G) (1-3785,default 3785): 3785
t
1
7
w

this line tells me how is big /dev/sda2 :

mb=$(echo pq | fdisk /dev/sda2 | grep "Disk /dev"| cut -f 5 -d \ )

the output returned is a string with a point inside,I can't accept it because ntfsresize accepts only numbers without floating points.

---

