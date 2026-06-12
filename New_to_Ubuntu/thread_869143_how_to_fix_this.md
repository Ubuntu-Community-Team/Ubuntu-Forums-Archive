---
title: "how to fix this?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Ginoxy on 2008-07-24
hello, i have this 

/////

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         191     1534176    6  FAT16
/dev/sdc2             192         487     2377620    6  FAT16


////

how to increase the end from 191 to another number ? as well as the other partition ?

---

### Post by Elfy on 2008-07-24
IF you change the sdc1 to be starting at 1 and ending at a number greater than 191 you will have to delete sdc2 first and then increase the size of sdc1.

It looks perfectly normal to me given the information in your post.

My sda is like this you can see the same pattern - not in order.

/dev/sda1   *           1        1302    10458283+  83  Linux
/dev/sda2            2676        9889    57946455    5  Extended
/dev/sda3            9890       10011      979965   82  Linux swap / Solaris
/dev/sda4            1303        2675    11028622+  83  Linux
/dev/sda5            2676        8605    47632693+  83  Linux
/dev/sda6            8606        9889    10313698+  83  Linux

Actual order sda1 - 4 - 2 - 3 , sda 5 and 6 reside inside sda3

---

### Post by Ginoxy on 2008-07-24
I dont think so ! as i want to install ubuntu into a flash drive USB flash 

and one of the steps asks for this : 

# Type fdisk /dev/sdx

    * type p to show the existing partition and d to delete it
    * type p again to show any remaining partitions (if partitions exist, repeat the previous step)
    * type n to make a new partition
    * type p for primary partition
          o type 1 to make this the first partition
          o hit enter to use the default 1st cylinder
          o type +750M to set the partition size
          o type a to make this partition active
          o type 1 to select partition 1
          o type t to change the partition filesystem
          o type 6 to select the fat16 file system
    * type n to make another new partition
    * type p for primary partition
          o type 2 to make this the second partition
          o hit enter to use the default cylinder
          o hit enter again to use the default last cylinder
          o type w to write the new partition table

now as you can see i can not set partition 1 to +750M 

but check this out see my partitions and tell me whats wrong 

[ATTACH]78809[/ATTACH]

both of thr partition are set for FAT16

is that right ? 
or should i change the 2nd one to linux-swap ? i dont know exactly

---

### Post by unutbu on 2008-07-24
Hello Ginoxy, 

Open a terminal and type

```
sudo /etc/init.d/hal stop   # It is good to stop HAL from automounting the drive
sudo umount /dev/sdc1
sudo umount /dev/sdc2
sudo gparted /dev/sdc

```
Use the GUI to resize the partitions. Click on sdc2 and then the Resize/Move button.
If the Resize/Move button is not highlighted, it means sdc2 is still mounted. If that is the case, right-click on the partition (sdc2) and select "Unmount". A partition can be mounted more than once, so you may have to click "Unmount" more than once, but not usually.

Anyway, after you have resized both sdc2 and sdc1, click the Apply button. Quit GParted.
Go back to the terminal and type:

```
sudo /etc/init.d/hal start  # Resume hal
```

> 
now as you can see i can not set partition 1 to +750M 

Why not? I see the Resize/Move button is not shaded, so you should be able to set it to whatever size you wish.

> 
both of thr partition are set for FAT16

is that right ?
or should i change the 2nd one to linux-swap ? i dont know exactly

Please post the link with the instructions.

---

