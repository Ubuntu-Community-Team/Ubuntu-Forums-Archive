---
title: "Super Newb - adjust partition size"
date: 2018-10-10
forum: New to Ubuntu
---

### Post by ksheby on 2018-10-10
I am  super new to ubuntu so I appreciate your patience/I prob wont use all the correct terminology but I am here to learn. A friend helped me set up my system last week. Im currently running ubuntu 18.04.1LTS off a 32gb USB drive. The way my friend set it up I can see that I have 3 partitions on the 32GB thumb drive. As I am adding a few bits of software I am seeing that the dev/sda partition is almost full and is only allocated 5.8gb of space, total. Is it possible / could someone walk me through adjusting the partitions to make a bit more room for software. I know 32gb is a kinda small but its what Im working with for now.

Thanks 
Kevin

---

### Post by DuckHook on 2018-10-10
Welcome to the forums, ksheby.

It's not that hard to change partition sizes, but it cannot be done from within that partition's working state. You will need a separate LiveUSB to do this. In other words, to change partitions in USB "1" you need to be running Ubuntu from USB "2".

Instructions: [https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions](https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions)

Most people who install onto a USB stick are doing so because they want to test Ubuntu. If this is your case, you may be better off just installing onto another 32-bit USB stick (they are ludicrously cheap these days) and devoting the whole stick to one partition. No need to split off / and /home into separate partitions. This way, you won't run into space issues. When working with small external drives it is usually a good idea to keep to one partition unless there are other concerns like encryption etc.

---

