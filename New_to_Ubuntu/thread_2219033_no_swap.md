---
title: "no swap"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by 20848 on 2014-04-22
new to ubuntu,
I have ubuntu 14.04 installed and i set a swap partition on my sdb drive. change size and change ext4 to linux-swap. but now if i start system monitor i don have swap. when i type sudo swapon -a it says: $ /dev/mapper/cryptswap1: stat failed: No such file or directory

i did the partitioning myself when installing with the do something else option.
can someone help me.

---

### Post by anaconda on 2014-04-22
> **20848 said:**
> new to ubuntu,
I have ubuntu 14.04 installed and i set a swap partition on my sdb drive. change size and change ext4 to linux-swap. but now if i start system monitor i don have swap. when i type sudo swapon -a it says: $ /dev/mapper/cryptswap1: stat failed: No such file or directory

i did the partitioning myself when installing with the do something else option.
can someone help me.

does 
sudo swapon /dev/sdbX
(where X is your swap partitions number) do anything for you?

If that didnt work:
You can re-format that partition to be swap by:
sudo mkswap /dev/sdbX
Danger!! That command WILLl destroy any existing data from the partition you use it on, so be sure that you only do mkswap on a partition that you are sure is your swap partition.

and then you can do the: 
sudo swapon /dev/sdbX

The command (in terminal)
free
shows your available memory including your swap...

IF that worked you can edit your /etc/fstab -file to mount your swap automatically. eg. with gedit editor:
sudo gedit /etc/fstab

You propably have  line like this in your fstab file:
UUID=4c7fd976-cf66-415a-841a-023a0759c842  none    swap    sw      0       0 

And you want to change it to 
/dev/sdbX       none    swap    sw      0       0 
(where the X is the number of your swap partition eg. 1 or 2 or 3...)

Note: Ubuntu uses UUID:S by default whit swap partitions. Sometimes it is better to use the older /dev/sdb3 -format. expecially in the case of swap partitions. Because each time you do the mkswap (or install another linux version) the UUID of your swap changes. the /dev/sdbX doesnt change.

---

### Post by anaconda on 2014-04-22
Oh. Just came to my mind.

Your problem might be just that the UUID of your swap-partition has changed (eg. if it has been re-formatted)
and that is why your swap entry in your /etc/fstab -file points to wrong UUID...

What I wrote above should still correct your problem...

---

