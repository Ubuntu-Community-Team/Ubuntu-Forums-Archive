---
title: "Newbie"
date: 2020-03-23
forum: New to Ubuntu
---

### Post by bobjesusiii on 2020-03-23
How do I allow myself access to the 1TB of storage I have? 

 [ATTACH=CONFIG]285261[/ATTACH]

---

### Post by spswitzer on 2020-03-23
Hey there and welcome.

You will have to provide the members a little more information for them to help you.  How you will be using it, is the storage internal or attached via USB or is it attached to your network? 

Cheers

---

### Post by coffeecat on 2020-03-23
@bobjesusiii, welcome to the forum.

Somehow you have managed to install Ubuntu to a root partition of 9.3 GiB, which is quite inadequate, and allocated a swap partition of 921GiB, which must be something of a record! A swap partition is not usually larger than the amount of available RAM. A swap partition is not "storage" in the normally accepted meaning of the word.

How did you manage to do that? Were you following a guide? The only sensible advice I can give is for you to start over. What you have is non-viable, and trying to get something usable from what you have now would take far longer than simply re-installing into a sane partition layout.

---

### Post by The Cog on 2020-03-23
Welcome to the forums.

You have that space all configured as a swap partition. You probably don't want that. First you need to stop using it as swap by opening a terminal and running the command:
```
sudo swapoff /dev/sda4
```
Then you can use gparted to shring the swap partition to just a few gigs (perhaps 2-5 G). 
The press Ctrl-R in gparted to refresh the view. It should allow you to create another partition (sda3). 
When creating the new partition, you can chose to make it an Extended partition which can contain several other partitions inside itself. This will allow you to create more partitions later if you want to. 
Then create another partition, this time a Logical partition (lives inside the extended partition). Choose ext4 filesystem.
Now you should have a disk icon on the left for this new partition. You should be able to double-click it to open it though probably won't have permission to write to it yet.
Use the command **lsblk** to show where it is mounted (probably /media/yourName/something). 
Then use this command to set permissions so anyone can read/write it:```
sudo chmod 777 /media/yourName/something
```
Assuming success with that, we can discuss making it mount somewhere sensible automatically when you boot up.

Edit. Beaten by CoffeeCat. He may be right. If this is a new install and you are a real newbie then it may be more comfortable to reinstall. And 9G is somewhat small for a system partition (nearly full already, 20-30G would be better), and you can only change the root partition size from a live CD (gparted can resize partitions but not a partition you are currently using.

---

### Post by SeijiSensei on 2020-03-23
Run the installer again. When you get to the discussion about managing disks hit "other" or "manual" at the bottom of the list of options.  Leave /dev/sda1 alone, but delete the other two partitions. Then create two new partitions, one of 30-40 GB that you will mount as the root filesystem ("/"), and allocate the rest to /home.  Format both of them with the ext4 filesystem. (You can do all of this using the GUI tool that comes with the installer.)

Now your home directory will be on the large partition, and you can put whatever you want there.

My root filesystem is 32 GB, of which ten are in use.

---

### Post by bobjesusiii on 2020-03-23
Okay so the storage is internal, it's my hard drive, and it's empty so I  don't need to worry about file loss, I've got all my stuff backed up. I've resized the swap partition to an appropriate size but I'm not able to allocate it to the ext4. I know I'm being thick but I really don't want to reinstall it.
[ATTACH=CONFIG]285262[/ATTACH]

---

### Post by deadflowr on 2020-03-23
When you right click on the unallocated space listing, does it bring up a dropdown with New at the top?
If so, click on New and it'll create the new partition in the unallocated space.
You can choose the file system type there. Then let it create it.

Of course, though, I'm not sure if you've tried this.

---

### Post by oldfred on 2020-03-23
Little key icons show your partitions as mounted. You cannot edit mounted partitions.
Better to use live installer & its gparted or a gparted ISO to edit partitions.

If not reinstalling you have to move your / (root) partition all the way left & then expand right into the unallocated space.
The move can take a bit, depending on amount of data. Any interruption will totally corrupt data and only way to recover then is from your backups. So have good backups. The expand into unallocated space should be pretty quick. Do not queue tasks but run one at a time.

Often better to keep / (root) as 25 to 30GB and then have a separate /home partition or partition(s) for data. Too large of a / is not optimal. Default install just uses / (and ESP if newer UEFI system), but use of just / was from years ago when drives were a lot smaller and then many users were dual booting, so / was typically not large.

---

### Post by bobjesusiii on 2020-03-24
I caved in and reinstalled, I don't have the technical knowhow yet, so I used someone elses computer to create a live usb. Thank you for your help folks!

---

### Post by daniewicz on 2020-03-24
No shame! Welcome to ubuntu.

---

