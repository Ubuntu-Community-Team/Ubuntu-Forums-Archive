---
title: "[SOLVED] Partition woes EeePC 901"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Maringouin on 2008-11-13
I'm a complete and absolute beginner with Ubuntu and I'm in a mess. When I installed Ubuntu on my brand new Eee PC901, I was startled to find a partitioner which is NOT mentioned in any of the instructions I read about installing Ubuntu (which made it all sound so easy). So I've made a mess, first trying to size partitions myself and then after about three more install efforts, I've wound up with this (using the 'Guided: use entire disk 4GB...'):

One partition is:
/dev/sda1 formatted ext3, mountpoint /
3.54 GiB, 2.31 GiB used, 1.23 GiB unused, flag: boot
/dev/sda2 extended, 219.64 MiB
which includes /dev/sda5 linux-swap, 219.61 MiB

The other partition is:
/dev/sdb1
filesystem ext3; label HOME; size 15.03 GiB
---and this is the part I don't understand---
Used 14.49 GiB, unused 548.21 MiB

But all there appears to be on the HOME partition is a 'lost and found' file and a 'user' file which contains 'My Documents' and a 'Trash' file and a file called 'tray.pid'

What is using up all the space? And how do I get rid of whatever it is? If I just use gparted to reformat the HOME partition to ext3, would that do the trick? I have no idea what the 'lost and found' file is and it won't tell me.

Ideally I would like to be completely rid of the whole partition thing and just have one partition for the entire hard drive but I don't know if that's possible; trying to get there is what has got me in this mess. If I just reformat the HOME partition so it's clean (all unused space), can I then use it as the place to store all my documents, music etc.? That's how I used to have my Windoze computer set up--system and programs on one partition and documents on the other. I could live with that.

Please help me because I can't really use this lovely new netbook until I have some space to use it. 

And please use really simple language. I'm perfectly capable of following clear instructions but I am absolutely and totally new to Linux and Ubuntu and don't know anything. Also a bit traumatised by all this!

Thank you all very much in advance.

---

### Post by sdowney717 on 2008-11-13
sda is one drive
sdb is another separate drive
So you have 2 drives in it?


Are you logging in and the system is working?
Is that user space really filled up?
goto places, home folder
select view hidden files from the menu
right click and how much is used space?
Also you can under applications, accesories send a screenshot.

---

### Post by mapes12 on 2008-11-13
> sda is one drive
sdb is another separate drive
So you have 2 drives in it?

No. The spec on the net indicates that this machine has a single Flash 20GB storage device. Not a mechanical HDD. I think the sda / sdb issue has been created by having Extended Partitions > /dev/sda2 extended, 219.64 MiB on the Flash device. 

The poster would need to use GParted (or equivalent) to make sure all partitions are "Primary" and not Extended. Then reinstall from there. /(root) on a separate partition and /home on a separate partition plus Swap.

Maringouin - What media are using to install Ubuntu and what guides are you following please?

**Alternatively,** > Ideally I would like to be completely rid of the whole partition thing and just have one partition for the entire hard drive but I don't know if that's possible;This is easy to do. Use GParted to delete all partitions. Then create one big ext3 partition for all the space. Then install Ubuntu again and when it gets to the "partitioning"section select "Guided-Use entire disk". The installer will then do everything for you. No need to think about partitions, Swap or the like. It will automate the lot. That will at least get you up and running and the /home bit on a separate partition can wait until another day.

---

### Post by Daveth on 2008-11-13
I assume you are using one of these

[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

remix is very nice- I have it on my 701. This is quite a nice and simple guide for you to follow

[http://www.simplehelp.net/2008/07/28/a-step-by-step-guide-to-installing-ubuntu-804-hardy-heron-on-your-eee-pc/](http://www.simplehelp.net/2008/07/28/a-step-by-step-guide-to-installing-ubuntu-804-hardy-heron-on-your-eee-pc/)

I used the usb stick method and it worked well. Once you have trashed the partition hell you are in, this should get you going.

---

### Post by Maringouin on 2008-11-15
Many thanks to you all for your prompt replies.

sdowney717, I was quite sure--as was mapes12--that this netbook has only one hard drive of 20GB.
But having tried everything to make one big partition following mapes12's instructions, I have found it completely impossible to amalgamate sda (4GB) and sdb (16GB) and I must conclude that they are indeed two separate drives. 
This would explain why, in installing, I get two 'Guided--use entire drive' options--one for the 4G ATA ASU-PHISON SSD drive and one for the 16GB ATA etc. SSD drive.

However, here's the situation now.

I cleaned off all the partitions and made two new ones, both Primary and both ext3, these were /dev/sda and dev/sdb.
This was the point at which I found that no matter what I did, I couldn't make everything into one big happy partition. So eventually I gave up and just reinstalled Ubuntu. I picked the 'Guided--use entire disk' for the 4GB drive when the partitioner came up.
Installation went fine.
I now have the same set up as I described in my first message,
WITH TWO IMPORTANT CHANGES:

(1) The /dev/sdb1 partition (filesystem ext3) now has no label in GParted; its size as given as 15.03GB of which 287.25 MiB is used and 14.75 MiB is unused--this is good, it's no longer reading as almost all used space.

(2) The /dev/sdb1 partition shows up in 'home' as '16.1 GB media', not as 'HOME' which it used to. There is a 'lost and found' file but no 'user' file (as there was when I first installed the system), and although I can mount the volume after giving my password, I can't do anything like create a folder, copy and paste, etc. I have checked the Permissions for the volume and it says that I'm not the owner so I can't change the permissions. The owner is given as 'root' and the group as 'root'.
In the user settings (under Administration), under the properties for my user Maringouin it says 'real name = root'.

How do I get permissions to use the volume?

Everything else on the computer seems to be working fine--printer, webcam, internet, Skype, sound etc. No problems starting up. 

Daveth, thank you for your kind and encouraging words. However I'm using ubuntu eee, which I understand is different from eeebuntu. Or so I have read elsewhere in the forums.

I would be grateful for your help in solving the permissions problem. I think I'm stuck with two partitions but that's fine as long as I can use them both!

---

### Post by silkstone on 2008-11-15
I'm running Ubuntu-eee (8.04.1) on a 901, and everything works fine. Perhaps I can help with how to set it up...

There are actually two physical SSD drives - a 4GB system drive and a 16GB data drive. Ideally, the OS and your programs should go on the 4GB drive as it is faster than the other one.

The easiest way may be to reinstall from the bootable USB stick with Ubuntu-eee on it.

Once you get to the partition section of the installation, choose Manual.

Then... Delete all existing partitions labelled sda and sdb. Don't touch sdc because that will be your USB stick!

Choose sda as / and format ext3.

Choose sdb as /home and format ext3.

There is no need for a swap partition, and many people recommend against swap on SSD as it can wear the drive out prematurely. It also takes up valuable disk space. Mine runs perfectly without it.

Go through the remainder of the installation procedure in the normal way, and everything should work. When you connect to the internet, you will be invited to upgrade tons of files - that's OK, although it will reinstall some applications (e.g. games) that were removed from Ubuntu-eee.

Note that there is plenty of spare space on the system drive (which will end up as sda1). I have a load of extra programs including Thunderbird, Bibble Pro, Google Earth and all the codecs, and I still have 1.1 GB spare.

Good luck!

---

### Post by Maringouin on 2008-11-17
O glorious day! O wondrous dream fulfilled!

Thanks, Silkstone, that appears to have done the trick. I appreciate the clarity of your reply which was easy to follow even for a by-now-slightly-terrified newbie!

My thanks again to everyone who took the time to reply to my post.

Cheers!

---

### Post by silkstone on 2008-11-17
I'm delighted it worked. :)

Just one more thing...

If you find that USB drives are not recognised, it will be because of a rogue entry in fstab caused by Ubuntu thinking that your installation USB stick was a CD!

In that case...

gksudo gedit /etc/fstab

Then either delete or comment out (with a #) the line with the cdrom entry, and save the file. Reboot and everything should be OK.

---

### Post by Maringouin on 2008-11-17
Brilliant, Silkstone, :KS indeed the problem was there! Thanks for thinking ahead!

---

### Post by sean32 on 2008-12-04
Just want to thank you silkstone. you solved all my problems too, And taught me a little more about the linux file system and partitioning.

---

