---
title: "Hard Drive Problem"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-04-07
Hi!
I formatted and installed Ubuntu 11.10 on my netbook today (finally got rid of Windows). Partitioned the disk following manuals and videos - One for Ubuntu, one 'swap' maybe? (for if the visual memory was occupied)  and the left over which was 126gb to use as my storage. 
I'm currently running Gnome and while I was trying to put all my information back from an external hard drive. It doesn't allow me. It shows 126gb free space and a folder that says Lost+Found - which I did not put there and neither do I have permission to see it's contents. 
When I try to copy it says that "It cannot be moved because I do not have authorization to copy" Neither can I create new folders or documents, so maybe it could be something simple as to change permissions, but I am relatively new to Linux and thought I'd ask you guys. 

Thank you

K.m

---

### Post by na5h on 2012-04-07
It sounds like you are trying to paste your files directly inside "File System". You are supposed to paste them somewhere inside your Home folder instead.

"File System" contains very important files and folders needed by your system. While it is possible to modify the contents of these files and folders, you shouldn't do it unless you know exactly what you are doing.

The Home Folder is where all of your personal files belong!

---

### Post by kabukiM0n0 on 2012-04-07
Yes, that is what I was trying to do. I understand now though!! Thank you!
One question I have from what you told me. 

Now it seems my 'home' folder has 30gb space and the system file 126gb ... is there any way to change this? as it was meant to be the opposite was round :/

---

### Post by Basher101 on 2012-04-07
could you run Gparted and make a screenshot of it? if you do not have it installed, you can get it in the Software center

---

### Post by kabukiM0n0 on 2012-04-07
There you go.

---

### Post by Basher101 on 2012-04-07
i kinda lost track of your post, my apologies.

In general, when you want to copy or move files you ususally cant, run nautilus with admin priviliges with the command ```
gksu nautilus
``` but be careful to NOT mess with system files. To change the rights of a file so you can view it, simply type ```
sudo chmod 777 /path/to/your/folder/or/file
``` this will allow any access (even for other users). I do not know all numbers and what they do with chmod, but setting 000 will lock them down so you cant open, copy, move, or do anything else with them.

p.s. your install partition seems to get full...try to not install too many programs on it

---

### Post by kabukiM0n0 on 2012-04-07
That's okay.

That's the problem, the partition which is full is the one where my home folder is located. i.e /dev/sda1 and /dev/sda6 is where all the software and computer files are - yet they were meant to be the other way round. 120gb for me and 30gb for the computer. Can this be altered? or is it too late?

---

### Post by Basher101 on 2012-04-07
to get this straight:

sda1 = only the home folder
sda6 = all the other system files etc.

---

### Post by kabukiM0n0 on 2012-04-07
> **Basher101 said:**
> to get this straight:

sda1 = only the home folder
sda6 = all the other system files etc.

Correcto mundo! :/

---

### Post by Basher101 on 2012-04-07
before i start suggesting things, what do you have on your home partition that takes so much space? Programs ususally install into /usr/share and /usr/lib ...

is it Music, Downloads, a bagillion pictures...

and, do you have an external Hard drive? or large USB sticks?

---

### Post by kabukiM0n0 on 2012-04-07
Exactly that. I have an External HD but I travel around a lot and don't carry it with me. That's why I need it the other way round.

---

### Post by Basher101 on 2012-04-07
well, if you have not made alot of installing on programs and many configurations and fixes, try to strip your home of all the data you want to keep to the external hdd and make a fresh reinstall...

From there you should make the partitions prior installing with a Live CD, if you want i could do that for you (i have helped some guys with remote control software on partitioning and installing before). Note that you can see everything i do while remote control is active for the case you think i would try to do something funny.

It is up to you to decide,
Copy the stuff and reinstall from scratch or
or...or...well you cant move the system files and expect it to work afterwards.

---

### Post by kabukiM0n0 on 2012-04-07
I guess it makes sense, having to re-install again. 
I can't do it this instant as the .iso file with the ubuntu is on an mp3 I'm missing the cable. But I haven't installed too much ...
How would the partitions have to be named so they would be the other way round?
- 30gb for the computer
- 4gb as a linux-swap 
- the rest for personal use

Is it the mount point or the device name which says which one does what?

---

### Post by Basher101 on 2012-04-07
the name indicates nothing, only when you open Nautilus you see at the left side names instead of numbers (e.g. System, Storage instead of 20 GB partition, 126 GB partition)
so you will have to focuse on the mount points. Make sda1 the "/" and place your home folder on sda**[COLOR="Red"]x[/COLOR]** it should be sda4 if i am right but don't bet on it..

p.s. i am currently on windows so i cant provide much help with gparted as i do not know it in and out to tell everything out of the blue (but enough to help you partition the hdd)

---

### Post by kabukiM0n0 on 2012-04-07
> **Basher101 said:**
> 
so you will have to focuse on the mount points. Make sda1 the "/" and place your home folder on sda**[COLOR="Red"]x[/COLOR]** it should be sda4 if i am right but don't bet on it..

That's how I placed the mount points. :/

It's okay, no rush; will be re-installing tomorrow.

---

### Post by oldfred on 2012-04-07
I usually suggest smaller system partitions and separate /home or /data partitions. All my / (root) are 20 to 25GB with only about 7GB used. But I move all the data folders to other partitions.

To be able to write to your data partition you just need to set ownership &  permissions. And if you add it to fstab it will be automatically mounted on every reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by kabukiM0n0 on 2012-04-08
> **oldfred said:**
> 
To be able to write to your data partition you just need to set ownership &  permissions. And if you add it to fstab it will be automatically mounted on every reboot.
You are spot on!! I went to the properties of the folder, and it states I am not the owner (for some reason) so I have no authorization in it. 
How do I do edit this though?

EDIT:I also noticed that said 126gb file, is inside systemfiles, in the data folder. so inside a 26gb partition I have a folder which is where my other partition sleeps ... :S

---

### Post by oldfred on 2012-04-08
It is in the link above on splitting home.

sudo mkdir /mnt/data
sudo chmod 755 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l


If the files & folders in the data partition are not owned by you, you can add a -R (recursive) to both chmod & chown , but be very careful not to do that to any partition other than your data partition. If you happen to change / (root) just reinstall. If you happen to change /home it might (only might) be recoverable. See man chmod and man chown for more info.

Edited to fix chmod just in case someone else sees this - see Morbius1 post below. Thanks Morbius1.

---

### Post by kabukiM0n0 on 2012-04-09
I read all the threads and found the one that applies to myself. 
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

I am still rather lost - My programming skill are not exactly advanced in any way. I shall fresh install and create "/" - "/home" and "Swap" and go from there ... this [i]should[i] fix the issue though from what I'm reading.

---

### Post by Morbius1 on 2012-04-09
I'm kinda confused by this topic. This can't be correct:
> Re: Hard Drive Problem
[QUOTE]Originally Posted by Basher101 View Post
to get this straight:

sda1 = only the home folder
sda6 = all the other system files etc.Correcto mundo! :/[/QUOTE]According to gparted sda1 is mounted to / and includes your home folder as well as "all the other system files". sda6 is mounted to /media and looks pretty much empty.

Get a listing of your home subfolders sorted by size:
```
du -sk * | sort -nr
```Then copy the biggest or all over to /media/data and either symlink or bind them back to the home folder. Am I missing something?

@oldfred, I think this is a typo:
>  sudo chmod 766 /mnt/dataDirectories always have to have odd numbered octal permissions. Even numbers don't set the "execute" bit and for directories that allows someone to open the folder to see what's inside. I think it should have been 755.

---

### Post by kabukiM0n0 on 2012-04-09
I seem to have solved the issue with doing a fresh install and mounting the system folder to "/" and my personal folder to "/home" 

Thank you all very much for the help! :D

---

