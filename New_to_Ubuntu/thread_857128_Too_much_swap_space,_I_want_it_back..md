---
title: "Too much swap space, I want it back."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Andread on 2008-07-12
Some months ago I installed Ubuntu over the XP partition, but being a newbie, when asked for the swap partition I choose to make it 30GB large!
I recently discovered that 1GB was enough.

While I want to keep using Ubuntu, I need to reinstall XP too, so I wonder if I can remove that useless swap partition (seems I can use a swap file on the Ubuntu partition) and use it to install XP.

Any idea on how to easily do this? :)

Thanks a lot.

---

### Post by Tom--d on 2008-07-12
You can Re size the swap space in Gparted.
```
sudo apt-get install gparted
```
System > Admin > Partition Editor

Unmount the swap.
Resize it. 
Mount it back.

Done :D

---

### Post by Andread on 2008-07-12
This was fast! Thanks!

But it returns this error:
Gtk-WARNING **: cannot open display:

Despite I'm on X windows ...

---

### Post by boblemur on 2008-07-12
i got that error once or twice, why i dont know.... if i recall try gksudo gparted

but i could be wrong...

---

### Post by Andread on 2008-07-12
Thanks so much guys, gksudo gparted worked.
Now I've managed to erase the partition.

---

### Post by ajgreeny on 2008-07-12
Not the best way, I'm afraid!  Run the ubuntu live CD which has gparted on it and will do the job much safer.  If you use the installed ubuntu, you will not be able to do anything to your root or home partition to make use of the space yopu have just freed, as both will be mounted, and gparted can not work on mounted partitions.

So run ubuntu live CD, open partition editor, right click on the swap partition and make sure it is not mounted, by clicking swapoff and reduce its size to what you want by moving the right end of it, probably, though how you change it will depend on the layout of your partitions.  1GB is usually more than enough for swap, as you say.  Now you can enlarge the root or home partition to use the space now freed up.

Unfortunately, this change to partitions and working on them may have changed your partition UUIDs (it may be just formatting does this, I can't remember) so check they are the same as your ubuntu menu.lst  and fstab files by using the terminal in the live CD and typing ```
ls -l /dev/disk/by-uuid
```Before you do any of this it would beworth doing that in your installed ubuntu and printing out the output so you have a note of UUIDs at the present, before working on partitions.  They may not change, but at least if they have you will know quickly from runningthat command in the live CD.

Good luck.

EDIT  OK you have deleted swap, but what will you do with the space now available?  You can add it to one of ypour current partitions by doing the last part of my suggestions or you can make a new partition and mount it with fstab an entry.

---

### Post by boblemur on 2008-07-12
im not really a ubuntu expert... but do you have any swap? 

if anyone could shed some light on weather its ok to not use swap space

---

### Post by quantumstitch on 2008-07-12
a little discussion about swap:
[http://www.linuxforums.org/forum/installation/34718-no-swap-space-oh-no.html](http://www.linuxforums.org/forum/installation/34718-no-swap-space-oh-no.html)

---

### Post by boblemur on 2008-07-12
cool thanks for that

---

### Post by Tom--d on 2008-07-14
Swap is used for when RAM becomes scares and for hibernation. 

There maybe more reasons. But I don't know them.

---

### Post by Dr Small on 2008-07-14
I have 300MBs of Swap, but none of it ever gets used. I may end up moving that space somewhere else eventually and just dumping swap, since I never *ever* get close to needing it.

---

