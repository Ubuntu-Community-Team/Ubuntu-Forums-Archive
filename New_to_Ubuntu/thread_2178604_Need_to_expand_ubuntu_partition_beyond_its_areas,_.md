---
title: "Need to expand ubuntu partition beyond its areas, gparted cant do it..."
date: 2013-10-04
forum: New to Ubuntu
---

### Post by Crinkle on 2013-10-04
Hello there, please take a look at this thought provoking image:

[IMG]http://i.imgur.com/wDVatqu.png[/IMG]

Is it possible to make my main linux partition bigger? I've tried using gparted and booting from the live CD but gparted simply cannot do it, You can "move" partitions, but only if you shrink them, at which point you can move them into the empty space you created by shrinking them, thats all. I want to physically join the free space before it onto it. Is it possible? Or would i have to format and lose everything?

---

### Post by Mark Phelps on 2013-10-04
Two things ...

First, you need to boot into Windows and run chkdsk on the NTFS partition.

Second, you need to expand the Extended partition, before you can expand the Ext4 partition.

---

### Post by Crinkle on 2013-10-04
Ok.... why do i need to go into windows? I probably cant anyway, its started randomly shutting off the pc at 5-10 minute intervals for no reason, hence... linux!

In regards to your second point, the extended partition IS the ext4 partition?

---

### Post by coffeecat on 2013-10-04
> **Crinkle said:**
> Ok.... why do i need to go into windows? I probably cant anyway, its started randomly shutting off the pc at 5-10 minute intervals for no reason, hence... linux!

Because gparted is showing an exclamation mark icon by sda2, meaning there is something wrong with it. Perhaps that's why Windows is randomly shutting down. Have you tried repairing it from a repair disk, or booting into safe mode by means of F8?

> **Crinkle said:**
> In regards to your second point, the extended partition IS the ext4 partition?

Have another look at your screenshot. Your ext4 partition is sda5, a logical partition. The extended partition is sda3. An extended partition is a special type of primary partition used only as a container for logical partitions. Mark Phelps is correct. You need to enlarge the extended partition before you can enlarge the sda5 partition. Also - you won't be able to do this from inside your running Ubuntu, which is what you have taken your screenshot from. You'll need to use gparted from the live CD.

Last point. Back up all important data before resizing partitions. There is the potential for something to go badly wrong.

---

### Post by Crinkle on 2013-10-04
Ok I've checked windows and it found and fixed some errors. But I still cant extend the sda3 partition, theres no available options for it from gparteds menus?

---

### Post by coffeecat on 2013-10-04
> **Crinkle said:**
> But I still cant extend the sda3 partition, theres no available options for it from gparteds menus?

Are you using the live session?

> **coffeecat said:**
> You'll need to use gparted from the live CD.

When you boot up the live session, the first thing it does is to automount the swap partition which prevents you from resizing the extended. Highlight the sda6 swap, right-click and select "Swapoff". Now highlight the extended partition and from the gparted menu, Partition -> Resize/Move. You can put in figures for the new size or there's the easier option of a slider at the top of the resize window. After you've adjusted the size, you need to click on the green tick apply button. Resizing an extended partition doesn't take long, but resizing an ext4 partition can take hours. 

And don't forget to backup first.

---

### Post by Crinkle on 2013-10-04
Ok that worked I now have the options, but none of them work, even extending it by a couple of megabytes gives the error @cant have overlappinmg partitions, even though the area its going into is empty space. :'(


By the way, no need to keep reminding me, i've already backed up everything important. Of course I've probably forgotten something somewhere, but thats always the way really!

---

### Post by Crinkle on 2013-10-04
Ok this seems to be nothing to do with the actual partitions at all, gparted just doesnt want to make this particular partition any bigger. I can create a new partition in the gap, using all of it up absolutely no problem. I can resize that partition and move it around, and delete it. But under no circumkstances will it attempt to resize the existing partition at all.

This is what gparted says:

[IMG]http://i.imgur.com/HEVNJwj.png[/IMG]

And the disk currently looks like this:

[IMG]http://i.imgur.com/JpFalgu.png[/IMG]

---

### Post by oldfred on 2013-10-04
You have to resize sda3 first and process that change (click on checkmark) so it includes the unallocated.
Then as a separate step you can move sda5 left. Then expand sda5 right. That may need to be two steps also.
Generally with gparted I do not queue steps anyway. I want each change processed before I try another.

Just to throw a monkey wrench in the works as another alternative.
I prefer smaller 10 to 25GB / (root) partitions and separate /home or separate /mnt/data partitions.  
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Crinkle on 2013-10-04
I thought about moving the home folder, but couldnt figure out how to do it before.

gparted isnt playing balls still, I CANT resize the **sda3**, even a bit, it gives that error message previously posted.

---

### Post by heir4c on 2013-10-04
If you can't resized the partition there is another option:
You can do a complete new install. 
So if you back-up your /home/*username* map (with all the hidden files, don't forget them) than you can delete sda6 sda5 and sda3 (in that order).
Than you have a hole new free space. Than make a new Extended partition and new partitions inside (If you want: for /, /home, and /DATA and a swap) and do a new install.(Or do it while you install Ubuntu) 
Than you can install all the programs you have installed on your old (write them down before you making any change to the partitions) and switch than the /home/*username* with your back-up.

After that it became like this:
sda1   Windows
sda2   Windows
sda3   Extended
----sda5    /
----sda6    /home
----sda7    /DATA
----sda8    swap

---

### Post by gedakc on 2013-10-05
To be able to modify partitions, GParted requires that the partition is not mounted or otherwise active.

The easiest way to do this is by booting your computer from removable media, such as [GParted Live]("http://gparted.org/livecd.php"), and using GParted.  In this way the partitions are not active.

---

