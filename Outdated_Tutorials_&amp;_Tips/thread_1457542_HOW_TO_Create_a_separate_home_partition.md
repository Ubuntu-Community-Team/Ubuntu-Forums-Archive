---
title: "HOW TO: Create a separate /home partition"
date: 2010-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by arrimapirate on 2010-04-18
After using openSUSE for a few years, i got used to having a separate /home partition instead of just a /home folder on the root drive. By default, Ubuntu only makes one partition (/) unless you create a partition setup when you initially install Ubuntu. Im going to show you how/why you can/should set up a /home partition after you install Ubuntu.

Advantage:
If Ubuntu for some reason crashes and becomes unbootable and unfixable reinstalling will not delete all of your important data and settings. You simply specify the /home partition to be mounted at /home when reinstalling.

Disadvantages:
Partitioning can end very badly if you dont know what your doing.
To help make this easier, everything we do will be done with a GUI. All of these steps can also be accomplished with the Terminal though.

Step 1: Boot into the live CD
Reboot your computer with your Ubuntu (or any live linux cd) in the cd drive and boot into the live system.

Step 2: Partitioning the hard drive
A. Start GParted from System->Administration->GParted
On most systems, /dev/sda is the main partition so we will work with that.

B. You should see all of the partitions on your hard drive. If you only have Ubuntu you will see 2: one is / and the other is swap. Right click on the / partition and select "Resize/Move" Shrink it to however big you wish you /home partition to be.

C. Now right click the free space (it will say unallocated and have a grey square) and select "New" Make it whatever file system you wish, label it something if you want to keep better track of it, and click "Add".

I recomend you double check what you have done up to this point, there  is no going back after step D

D. To commit all these changes, click the check mark at the top of the program (it says "Apply all operations" if you hold your mouse over it)  This will repartition your hard drive.

Step 3: Reboot and add fstab entry
A. Reboot your computer without the live cd in the drive. Log in as usual. If you have anything important in your /home folder, i recommend copying it to an external of the root drive so you will be able to add it back once you are done setting up the /home partition.

B. Install Storage Device Manager by [FONT=monospace]going here [/FONT]http://packages.ubuntu.com/pysdm
[FONT=monospace]and [/FONT]clicking the version that is for your version of Ubuntu. This will allow you to edit you fstab file and allow the new partition to be mounted as /home. 

C. Start Storage Device Manager by going to System->Administration->Storage Device Manager

D.  Click the dropdown arrow next to /dev/sda (or whichever hard disk your partitions are located on) and select the newly created partition. If it asks if you would like to configure it click yes.

E. Next to Mountpoint, click the folder icon and goto File System (your root drive), click the home folder and then click open. This will assign the new partition a mount point at /home.

F. Next to options, click the set defaults button. This will mount the partition at boot.

Step 4: Reboot and enjoy
A. Reboot your computer and log into your account. You will have to set ownership of the /home folder with sudo chown YOURUSERNAME /home/YOURUSERNAME before you can copy your files and folders onto it.

B. Done!

Feel free to post any questions comments or problems you may have, i will be more than happy to help out!

---

### Post by Foster Grant on 2010-04-20
You can also do this by choosing the "Manual" partitioning option in the Ubuntu installer on the LiveCD. The installer takes care of all the dirty work for you.

[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by mistrynitesh on 2010-04-21
> **arrimapirate said:**
> 
....
Step 3: Reboot and add fstab entry
....
B. Install Storage Device Manager by [FONT=monospace]going here [/FONT]http://packages.ubuntu.com/pysdm
[FONT=monospace]and [/FONT]clicking the version that is for your version of Ubuntu. This will allow you to edit you fstab file and allow the new partition to be mounted as /home. 
....


I wonder why you suggest the users to install the package by going to packages.ubuntu.com/pysdm. The easier and officially suggested way is use Synaptic/apt-get/aptitude. Also in case you want the users to go via website, in that case, you need to add a few more steps like >download the package; >Right-click on downloaded package; >Click Install; etc.

Also a straight-forward way of doing Step 3 (a subjective matter) would have been to:
>Open the /etc/fstab file as root
>Add the following line in the end:
 ```
/dev/sdxy /home ext4 defaults 0 0
```
 (where 'sdxy' is the partition you just created)
>Save and close file
Tada!


Bye the way, nice work :)

---

### Post by Jerubaal on 2010-05-07
I have two installations of 10.4: an upgraded one with all my settings and /home built in, and a clean install on a new drive.
I have several partitions lined up to act as /home, /backups and /multimedia and so on.

Question 1: Can I just copy everything under /home into the /home partition? (Including .folders) Is there anything that would be missed by doing this? Will this mess things up because the clean install does not have all the programs that the  upgraded copy has?

Question 2: Is it advisable to also have a /usr partition? If so, what does it contain and how big a partition is recommended?

---

### Post by arrimapirate on 2010-07-09
> **Jerubaal said:**
> I have two installations of 10.4: an upgraded one with all my settings and /home built in, and a clean install on a new drive.
I have several partitions lined up to act as /home, /backups and /multimedia and so on.

Question 1: Can I just copy everything under /home into the /home partition? (Including .folders) Is there anything that would be missed by doing this? Will this mess things up because the clean install does not have all the programs that the  upgraded copy has?

You will have to chown the files after you copy. I can explain how but i need to know if the installs are on the same machiene and if you plan to use the same user name.

> **Jerubaal said:**
> Question 2: Is it advisable to also have a /usr partition? If so, what does it contain and how big a partition is recommended?

I dont know a lot about the /usr folder other than that it contains some source files, binary files and shared binary files. Placing it on a seperate partition shouldnt cause any problems unless it fills up. On the upgraded install, check the size of the /usr folder. Id say make the partition something close to that size.

---

### Post by jimboss on 2010-09-30
In case anyone wants to do this to make their files readable by windows, take note that fat32 cannot (really) be used as the system type (I made this mistake) because of permission errors!

My solution to this was to create a separate fat32 (or vfat in linux speak) drive with photos, videos, and work on. I mounted this to an empty folder /shared for booting (editing fstab appropriately). Then the individualy folder (Photos, Work etc...) were symbolically linked to directories in my /home/username/. This worked really nicely! The fat32 partition is also automatically mounted by windows (7) when booted.

The guide I used for making partitions etc was :

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

A good addition to what's written above is, once you have a free partition, to do the copying etc from the normal boot, then you can test your mounting directly (mount-a), although if you've made a new /home partition you may get more problems on booting (especially if you don't chown certain files, perhaps all). Make sure you are careful with the copy and maintain things the same as much as possible - permissions, changed dates, etc... 

Yeah well, I think partitioning the file-system up is good if only to help you understand how the operating system works (or at least that's how it's helping me!)

As a final note, maybe because of my first attempt to make a fat32 /home drive, I couldn't even make an ext4 /home drive using my backed-up /home (without applet errors on logon - maybe you can sort that out though), so I gave up pretty fast and just re-installed ubuntu (it was a brand new installation anyway, pretty much a waste of time to try and move the /home folder!). So, watch out!

---

