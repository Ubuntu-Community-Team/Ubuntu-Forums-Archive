---
title: "Reinstalling Ubuntu 11.10"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by Future Warthog on 2012-04-08
I kinda messed up my system, and I am working on fixing it.
I also have Windows XP Professional installed on the computer as well, and I don't have the install disk, so I can't wipe my HDD.
Is there any way I can wipe ONLY Ubuntu stuff and reinstall? I want to know I case I really mess up my system beyond belief.

---

### Post by Basher101 on 2012-04-08
You can, but you must do the partitioning with care, or you will somehow mess up somewhere and render your Windows useless..

Before we proceed further, pop in a Ubuntu Live CD/USB and "Try Ubuntu" until you reach the desktop. From then on you search and run the program "Gparted" <- it is the partitioning tool you will use. Just open it, do not do anything now, just make a screenshot and post it here in the thread. 

From there on I will give you further instructions.

---

### Post by Future Warthog on 2012-04-08
Ok, the only thing is, I installed Ubuntu alongside Windows. Is that a problem?

---

### Post by Basher101 on 2012-04-08
> **packpatfan said:**
> Ok, the only thing is, I installed Ubuntu alongside Windows. Is that a problem?

not at all.

---

### Post by Future Warthog on 2012-04-08
pheew. I don't need to do it now, I just want to be sure if it is possible.
Could you give a general overview of how to do it?
Also, is it possible to uninstall Ubuntu from within Windows XP?

---

### Post by Basher101 on 2012-04-08
from within XP...not sure if XP has a built-in partitioning program, but any partitioning program should do the work...you would just delete the linux partition(s) and extend your windows partition to use the new free space.


How to fix:

1. Run Live CD session,
2. Run Gparted and delete the ubuntu partitions and create new ones,
3. Run the installer and assign the mount points (where your system files are going to be installed)
4. Follow the installer, create a username, password...reboot and maybe adjust some things with the Grub config (e.g. which OS to boot by default).


Regards


p.s. you can mess up at step 2. - 3. to render Windows useless.

---

### Post by Future Warthog on 2012-04-08
Ok, but what is the Ubuntu partition? and how do I assign a mount point?
Sorry for all the questions, but can I just do gparted from within Ubuntu that is installed for the screenshot?

---

### Post by Basher101 on 2012-04-08
its done with a custom installation (e.g. making the partitions yourself first using Gparted and then assigning the mount points within the installer program) 

the Ubuntu partition is the sector that holds your "/". That means all the system files, sub-directories, your home folder and all the settings.

Since you are not rushing it, write me a PM and give me a Screenshot of your partitions for further instructions and support.

regards

---

### Post by Future Warthog on 2012-04-08
Here is the Screenshot from gparted

---

### Post by Basher101 on 2012-04-08
> **packpatfan said:**
> Here is the Screenshot from gparted

use the attachment option to upload it

---

### Post by Future Warthog on 2012-04-08
Sorry, here it is.
/dev/sda2 is my attempt at installing Ubuntu on a seperate partition, but it didn't work.

---

### Post by Basher101 on 2012-04-08
your Ubuntu partition is inside the extended one. So you have 2 options:

1. delete the current Ubuntu partition and just re-use the SWAP partition and keep the **[COLOR="Red"]sizes[/COLOR]** of all the partitions in there the same 

or

2. delete the whole extended partition and set new sizes for the Ubuntu partition, SWAP (swap should be the same as before) and that NTFS partition.

Do you have a lot of important data on that NTFS partition? If not you can consider option 2.

---

### Post by Future Warthog on 2012-04-08
> **Basher101 said:**
> your Ubuntu partition is inside the extended one. So you have 2 options:

1. delete the current Ubuntu partition and just re-use the SWAP partition and keep the **[COLOR=Red]sizes[/COLOR]** of all the partitions in there the same 

or

2. delete the whole extended partition and set new sizes for the Ubuntu partition, SWAP (swap should be the same as before) and that NTFS partition.

Do you have a lot of important data on that NTFS partition? If not you can consider option 2.

So if I wanted to totally wipe Ubuntu and start over, I should delete EVERYTHING in the highlighted partition in the image included?
About the send NTFS partition, no. I would like to empty it and install Ubuntu on it.

I actually want to entirely reinstall Ubuntu now.

---

### Post by Basher101 on 2012-04-08
may i suggest a setup (that I myself use) ?
Instead of giving Ubuntu the whole space, just give it 15-20 GB and use the rest as a shared storage for both Windows and Ubuntu. Store your movies, downloads, documents and whatnot there to not have 2 copies of each on both Windows and Ubuntu.

---

### Post by Future Warthog on 2012-04-08
> **Basher101 said:**
> may i suggest a setup (that I myself use) ?
Instead of giving Ubuntu the whole space, just give it 15-20 GB and use the rest as a shared storage for both Windows and Ubuntu. Store your movies, downloads, documents and whatnot there to not have 2 copies of each on both Windows and Ubuntu.

So, delete the Extended partition and 2nd NTFS partition entirely, and then create a partition with 15-20 GB of space, and create the mount points for Ubuntu in there, and then install Ubuntu within that, putting the remaining space into a separate partition for storing items I want on BOTH systems?

(puff, puff)

---

### Post by Basher101 on 2012-04-08
> **packpatfan said:**
> So, delete the Extended partition and 2nd NTFS partition entirely, and then create a partition with 15-20 GB of space, and create the mount points for Ubuntu in there, and then install Ubuntu within that, putting the remaining space into a separate partition for storing items I want on BOTH systems?

(puff, puff)

pretty much, yes^^

it is somewhat unpractical to have 2 copies of frequent used files..
and 15 GB should be plenty. A fresh Ubuntu install takes 4,3 GB, with updates and some programs it should be around 6,5 GB. So you got some air for more.

p.s. in general if you have kernel updates, and the newer kernel works without any major bugs be sure to remove the olds ones. A kernel takes about 100-150 MB of space (which is quite alot for Ubuntu standards). Currently the updates are not larger than 5-10 MBs. Try getting that low on Windows :D

---

### Post by Future Warthog on 2012-04-08
That makes sense. Thank you SO much! I really messed up my system, so I need to reinstall it.

---

### Post by Basher101 on 2012-04-08
> **packpatfan said:**
> That makes sense. Thank you SO much! I really messed up my system, so I need to reinstall it.

why praise the day before the night? :D Its the same like eating the corn before planting it. First you have to pull it off before starting to cheer :popcorn:

p.s. if in doubt, i can do the partitioning and installing for you. I have done so via remote control using Team Viewer on a live CD (you use the live cd not me :D) to help some newbies that had 0 expirience with partitions to install Ubuntu so they dont mess it up due to lack of expirience.

---

### Post by Future Warthog on 2012-04-08
well, I was wondering how to do that, so that is what I was thanking you for.

---

