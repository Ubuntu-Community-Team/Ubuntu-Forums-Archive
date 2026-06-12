---
title: "nwe sata HD issues"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by taith on 2008-05-07
not sure if this' the right place, but since ya'll are always so helpful, i figured whynot :)

i have just bought a new harddrive, when my old one is connected, it'll boot no problem, 

when only the new connected, it says the drive was not able to be added onto the partition table. :( i can boot into digital dolly, but it cannot find any partitions either.

when both drives are connected(old as SATA-0), ubuntu loads properly, but the new one wont show anywhere.

any ideas why this may be happening?

---

### Post by jimv on 2008-05-07
If it's a new drive, it needs to be formatted and partitioned before you'll be able to see anything on it.

The best way to do that is to install Gparted in Ubuntu.

TO get it, just type this in a terminal:

sudo apt-get install gparted

Now you should have an icon for Partition Editor under System>Adminstration.  With both drives plugged in, open the Partition Editor up.  On the top right is a pull down menu that will allow you to select which drive you want to edit.  The new one is going to be the one that doesn't have any partition info yet.

Once you have your new drive selected, click NEW in top left.  That will bring up the New partition creation window.  I think by default it uses the entire drive for the partition, so all you will have to do is choose which file system you want.  That's would be either FAT or Ext3.

Of course, that's my suggestions, you can partition it however you want.

---

### Post by taith on 2008-05-07
i understand how it will need to be partitioned before i can use it... however, the drive isnt getting added onto the partition table... i cant see it in ANY partition managers...

---

### Post by taith on 2008-05-07
anyone have any ideas? how to make my new harddrive appear?:(

---

### Post by jimv on 2008-05-07
YOu need stronger magic.

The only thing I can think of is that maybe you have a SATA 3Gb drive and your SATA ports on your motherboard only support 1.5Mb.

---

### Post by taith on 2008-05-07
i knew it... :) HAHA

seriousally speaking tho... the new HD is 3.0 gb/s... where would i be able to see if the ports are 1.5?

i would assume the only way to upgrade them to 3.0 would be a new motherboard?

---

### Post by jimv on 2008-05-07
Do you know the model of the motherboard?

---

