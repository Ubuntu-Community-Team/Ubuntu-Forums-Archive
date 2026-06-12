---
title: "Fixing a mp3 player with Ubuntu"
date: 2007-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by alienseer23 on 2007-09-21
So, I got my hands on an ipod nano clone from china. It was advertised as an 8 gigabyte mp3 player. 

I opened it up and here are the specs:
...............................................................................................................................
firmware:
act209x_s75_cy           (actions company ltd)
9.0.50

memory chip:                 (65nm 8Gb MLC NAND Flash)
samsumg 701 
k9g8g08u0m
pcbo
fe3781

battery?:
rp432030p
200mah
3.7v

processor:                     (Actions Company, again)
ATJ2093H
FC126FA 5CH
...............................................................................................................................

I did some google-ing and found that it was an 8gbit chip, ie., only one gbyte.
Problem was it showed up on all of my machines as an a gbyte, and this was causing some serious problems with playback, mounting file transfer, you name it!

If you have an mp3 player or a flash memory device of ANY kind that you think is hacked (showing more memory than is actually there) then this is for you.
If you have a bricked (dead) mp3 player or flash drive, try this, it may help.

For those of you who know, all you need to do is use fdisk to write a new blank partition table, and then format that partition (fatxx for most mp3).
For those of who who just went, "Huh..f-whah?..partition who?" this is for you.

1) for best measure go into ->system--->preferences--->removable drives and media. Make sure that "mount removable drives when hot-plugged" is unchecked. You want your player connected, but unmounted for his process.

2) BEFORE plugging in your device go to ->applications--->accessories--->terminal

3) type in "sudo fdisk -l"
this will show all disks ad partitions on your system. Take note of what is there.

2) power on and plug in your device.

4) type in "sudo fdisk -l" again.
this will show all disks ad partition on your system, again. Find the one that is your player or flash drive, it will be the new disk on the list. More than likely listed last.  BE CAREFUL, if you select the wrong drive, you could kill your installation or, at the least  loose a lot of data!
let's say it is "/dev/sdf" and there is one partition "/dev/sdf1"

5) in the terminal type in "sudo fdisk /dev/sdf" (you will replace 'sdf' with whatever your drive showed up as)
now you are in fdisk.
why not type in "m" for a list of commands? It never hurts to be familiar with the packages on your system, particularly the very handy ones like fdisk!

6) now type in "o"
this will write a new blank partition table to your drive. The partition table is what the makers of "hacked" mp3 players (or flash drives) manipulate to show that they are bigger than what they actually are.

7) type in "w"
this will execute the writing of the information you ordered in step 6.
you will now be booted out of the program, back into your regular terminal.

8) for safe measure, unplug and reboot (power off, and power back on) your player (or flash device). Then plug it back in.

9) now type in "sudo fdisk -l" once more. Locate your device again; it may have a new name, where is was "/dev/sdf" before, it may now show up as "/dev/sdg". If it was hacked, you will see it has a new, much smaller size.
Don't blame me, I suggest you call for a refund! Often you will get at leaste a partial.
If you got your device off ebay, BLACKLIST THE SELLER!!!

10) you can use the fdisk program to create and format a new partition.
or you can use gparted or qtparted. I like gparted alot, so
in the terminal type in "sudo apt-get install gparted".

11) once installed, go to ->system--->administration--->Gnome partion Editor

12) WITHIN Gparted go to ->Gparted--->Devices--->(YOUR DEVICE HERE)

13) go to ->partition--->new 
      leave it as primary
      select fat32 for an mp3 player. With a flash drive you can use your choice.
      use the entire drive.
you will notice here, aslo, that you see a new size for your player or flash drive. If you do not see the new size, try again, make sure you follow all of the steps.

14) once partitioned, remove, reboot, and plug it back in again.

15) let's make sure we did it right by typing in "sudo fdisk -l" again. 
your device should be listed with a partition that is fat32, or whatever you used.
If not, try again, make sure you follow all of the steps.

if it shows up properly, congrats! You just "unhacked" your mp3 player and can now use it with glee!!!
:guitar:
If you want o revert step one, do so, and unplug and replug in your device, it should mount right up, and you can now drag and drop,  or use amarok or whatever to fill that puppy up!

I could have had you use fdisk exclusively \, but in using 2 different programs I have done two things for you. One is that you get confirmation from multiple sources that you are doing the correct thing; and two, you now are familiar with two great programs for disk and partition management, may they serve you well!

Here is a link to a forum sight devoted to hacked players and knock-off player support:

[http://www.mympxplayer.org/](http://www.mympxplayer.org/)

it is a primarily windows oriented forum, but I know some people could use some support there for linux! You can find info there on firmware support, manuals, and sign a petition, see seller blacklists and all sorts of stuff, check it out!

I hope this tutorial was helpful to you, if it was, please leave a comment!
And you can come visit me, and the rest of the ubuntu-michigan team on irc. We are on freenode at "#ubuntu-michigan"

---

