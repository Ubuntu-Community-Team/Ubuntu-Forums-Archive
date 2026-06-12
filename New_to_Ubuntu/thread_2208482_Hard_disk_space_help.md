---
title: "Hard disk space help"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by james104 on 2014-02-28
Hello all,

I'm in a dilemma, I am really happy and impressed with Ubuntu, it's running my football manager game like a dream.

I have windows 7 on my laptop and chose to dual boot it and then use ubuntu solely for FM and maybe surfing the net as Ubuntu boots PDQ and gets to desktop quick too. 

Windows is then used for everything else, PShop, MS Office and importantly (being an iphone user) I tunes!

Now I allocated 14gb for Ubuntu as I had 43gb remaining so wanted to be sure I wasn't leaving too little room on either side- I was unaware you can access the windows partition thru Ubuntu so it's not like I can't store bits around the place...anyway... I allocated the 14gb which technically ended up as 9-10 gb prob due to storage on hard disks and I am now constantly getting warnings about low disk space (300-400mb)

I wish to simply resize my Ubuntu partition to increase it to 20-25gb which is what I should have done from the start! 

Given I'm posting here you can gather im an Ubuntu/Linux noob!

How can I simply increase the size of the partition so I have plenty of storage without having to lose data etc?

---

### Post by sandyd on 2014-02-28
Hi, can you post the output of
```

sudo fdisk -l
```
This will allow us to view your current partition setup, and allow us to figure out how your partitions should be adjusted.

---

### Post by james104 on 2014-02-28
Thank you for your quick response! :)

james@Bumblebee:~$ sudo fdisk -l


Disk /dev/sda: 160.0 GB, [160041885696]("tel:160041885696") bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47c7fe89


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     [1536000]("tel:1536000")   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   285241069   141083511    7  HPFS/NTFS/exFAT
/dev/sda3       285241342   312580095    13669377    5  Extended
/dev/sda5       285241344   308408319    11583488   83  Linux
/dev/sda6       308410368   312580095     2084864   82  Linux swap / Solaris
james@Bumblebee:~$

---

### Post by sandyd on 2014-02-28
Can you also post the output of
```

df -h
```
thanks.

---

### Post by james104 on 2014-02-28
> **sandyd said:**
> Can you also post the output of
```

df -h
```
thanks.

Hello I'm afraid I cannot get a successful output to the command sudo df-h ?

---

### Post by oldos2er on 2014-02-28
You're missing a space between df and -h: ```
 df -h
``` Also there's no need for sudo.

---

### Post by james104 on 2014-03-01
Shall try this a little later so, open terminal type df -h 

:)

---

### Post by Mark Phelps on 2014-03-01
Couple of words of caution (from experience:)
1) Do NOT use GParted to shrink down your Win7 OS partition if that is where you end up having to get more space for Ubuntu.  Doing that risks corrupting the Win7 OS filesystem and rendering it unbootable -- making it really hard to fix.
2) Do not write to your Win7 OS partition from inside Ubuntu.  Writing to a data partition is OK,  but writing to an OS partition again risks file corruption.

---

### Post by james104 on 2014-03-01
Ah ok, I've only copied a few files back and forth between windows and Ubuntu. I have read somewhere that using the Linux partition tool is bad for windows. And yes it will be a case of needing to shrink the windows one to make room for more Ubuntu to claim it. In hind sight I should have created a blank 10-15gb partition separate to windows and maybe then get that into Ubuntu!

---

### Post by james104 on 2014-03-01
Hello,

The above requested command gives the following info;

james@Bumblebee:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        11G  9.8G  438M  96% /
udev            987M  4.0K  987M   1% /dev
tmpfs           399M  868K  398M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            996M  152K  996M   1% /run/shm

---

### Post by sandyd on 2014-03-01
> **james104 said:**
> Hello,

The above requested command gives the following info;

james@Bumblebee:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        11G  9.8G  438M  96% /
udev            987M  4.0K  987M   1% /dev
tmpfs           399M  868K  398M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            996M  152K  996M   1% /run/shm

Heres the issue - your ubuntu installation is inside an extended partition - which will need to be resized once your Windows partition is shrunk within windows.
Then, your ubuntu partition will need to be expanded to the left (gparted).

That is an issue - because expanding to the left requires that gparted copy the entire Ubuntu installation (risky)

What you can do is create a new partition after resizing ( you havent hit the 4 partition limit of MBR yet!) and use that as your home folder.

Can you open a terminal and post the output of
```
du -sh
```
That will show you the size of your home folder.
It might take a while to run.

---

### Post by james104 on 2014-03-03
> **sandyd said:**
> Heres the issue - your ubuntu installation is inside an extended partition - which will need to be resized once your Windows partition is shrunk within windows.
Then, your ubuntu partition will need to be expanded to the left (gparted).

That is an issue - because expanding to the left requires that gparted copy the entire Ubuntu installation (risky)

What you can do is create a new partition after resizing ( you havent hit the 4 partition limit of MBR yet!) and use that as your home folder.

Can you open a terminal and post the output of
```
du -sh
```
That will show you the size of your home folder.
It might take a while to run.

james@Bumblebee:~$ du -sh
6.2G	.
james@Bumblebee:~$

---

### Post by james104 on 2014-03-04
Having posted the above I then decided to use windows disk management to shrink my windows partition. This has freed up 15gb now!

my next question do I need to allocate that extra partition to Ubuntu? When I'm into Ubuntu that disk manager shows the additional even tho I've done nothing!

so in other words do i need to do anything now or should I be doing something to ensure Ubuntu utilises the extra space I gained?

---

### Post by james104 on 2014-03-13
Hello,

So now that I have some space freed up on my windows install having shrunk the volume I need to allocate this to Ubuntu. Could someone please provide some simple steps to allow me to do this?

I have read about booting ubuntu of a memory stick and running GParted or something similar. Is this the best way?

---

### Post by sotiris2 on 2014-03-13
Can you give us fdisk -l again? 

We can either extend the partition to the free space or make a new one to host your **/home** folder. The first will definitely require a bootable media (usb stick/dvd) the second not but in both case having one in hand is handy.

---

### Post by james104 on 2014-03-13
Hello,

bootable Ubuntu memory stick in place in preparation.

I had to not install some updates yesterday as there wasn't enough room!

Command output:

[COLOR=#000000][FONT=Calibri]Disk /dev/sda: 160.0 GB, 160041885696 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Disk identifier: 0x47c7fe89[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]/dev/sda2   *     3074048   254519021   125722487    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]/dev/sda3       285241342   312580095    13669377    5  Extended[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]/dev/sda5       285241344   308408319    11583488   83  Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]/dev/sda6       308410368   312580095     2084864   82  Linux swap / Solaris[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]james@Bumblebee:~$
 
And just in case

james@Bumblebee:~$ du -sh
6.1gb[/FONT][/COLOR]

---

### Post by sotiris2 on 2014-03-13
Ok do you have Gparted installed in your system? If not

 ```
sudo apt-get install gparted
```

Run gparted. Locate the unallocated space on the partition list or graph. Right-click on it and select **New**. 

Select ext4 as the filesystem. Make sure it's as big as possible and press **Add**.

Click on the green check button (apply all operations) and wait till it's done. 

A new icon for it should appear in your launcher so you can access it easily. 

Open your home folder and go up one level (alt+up arrow if no button). You should see a folder with your username and a house icon. Copy (don't cut or remove yet.) that file to your new partition. After it's done double-check file size and files count via right-click => properties. Also check in Permissions tab that the owner is **you**.

Open **Disks** (search from dash dont put in terminal). Locate your new partition in the graph, select it and click on the gears button below them, select **Edit mount options**.
 
Disable ** Automatic mount options ** if it's enabled and make sure the following are set.

Mount at startup **is** checked, the other two **not**.
In the 3rd text field which curiously has no name (its above mount point and probably filled with a lot of stuff seperated by commas). Delete everything there and put **defaults** 

On text-field **Mount Point** put **/home** (with the **/**)
Don't touch Identify as. 
Filesystem Type should read **ext4**.

Press ok and authenticate.

Now double-check everything again. If all are ok you can delete your original user folder. (the one with the house icon in the full partition). Do **NOT** delete the actual /Home folder, just the one with your username that's inside. 

Reboot.

If you have any doubt's regarding my instructions feel free to post back before implementing I 'll be online for some time.

---

### Post by james104 on 2014-03-13
Hello,

Thank you very much, I have got as far as copying the home folder onto the new partition however root is the owner and not me, how would I take ownership of this partition?

---

### Post by sotiris2 on 2014-03-13
Right click on the copy and find its locations via properties. Copy that and paste it here please. It probably would start with /media.

---

### Post by james104 on 2014-03-13
Hello,

My home folder says: folder (inode/directory) but I guess you dont mean this?

My new 16gb partition only has a folder called lost and found... this is the one with permissions that show the owner as root..
 
** To clarify I was unable to paste my copy onto the new partition..

**UPDATE

Right clicking new partition and selecting properties shows /media

The folder within called lost and found shows /media/286ac7f7-c384-4af8-bdf1-5aab0951f491

---

### Post by sotiris2 on 2014-03-13
Ok. Did you try to copy your home folder to the new partition? 

If it does not let you:
Open a terminal (Ctr+Alt+T) and input gksudo nautilus. *Input your password.* It will open a files window. Use this to copy your home folder to the new partition. 
After it's done right click on the new folder and find its location. Its the 4th field, it has Location: something/something/ . Need to copy that and paste it here for me. 
In any case do not proceed with anything else if you can't complete this. Just come back for more help.

---

### Post by james104 on 2014-03-13
Hello,

Thanks,

It is still copying but is in this location /media/286ac7f7-c384-4af8-bdf1-5aab0951f491

---

### Post by sotiris2 on 2014-03-13
**When its done** open a terminal again and input

> sudo chown -R **user**:**user** /media/286ac7f7-c384-4af8-bdf1-5aab0951f491/**user**

Where user should be your username, which should be the same as the file you are copying. The terminal will ask you for a password. Just type it normally , it works although it won't show anything on screen, and press enter. 

Then confirm that you became the owner of the copy. After that continue from the instructions in my big post from: Open Disks

---

### Post by james104 on 2014-03-13
Thank you, the command complained the user was invalid but I was able to change the owner using the permissions tab under properties. Will this be sufficient?

---

### Post by james104 on 2014-03-13
> **sotiris2 said:**
> Ok do you have Gparted installed in your system? If not

Open **Disks** (search from dash dont put in terminal). Locate your new partition in the graph, select it and click on the gears button below them, select **Edit mount options**.
 
If you have any doubt's regarding my instructions feel free to post back before implementing I 'll be online for some time.

Hello again... sorry! So close! 

I cannot seem to get to an app called Disks. I see Disk usage analyser but this only shows folder structures not the disk itself to set options on.

---

### Post by sotiris2 on 2014-03-13
Maybe its not installed by default. Try gnome-disks on a terminal.

If its not installed do

sudo apt-get install gnome-disks

Also make sure all files inside are as well owned by you. This is the reason i gave a terminal command since it would certainly do so. I reccomend running the command again. To be sure of your username type whoami in terminal (without sudo).

---

### Post by james104 on 2014-03-13
> **sotiris2 said:**
> Maybe its not installed by default. Try gnome-disks on a terminal.

If its not installed do

sudo apt-get install gnome-disks

Also make sure all files inside are as well owned by you. This is the reason i gave a terminal command since it would certainly do so. I reccomend running the command again. To be sure of your username type whoami in terminal (without sudo).

Hello,

Still same invalid user message. Also get this

james@Bumblebee:~$ sudo apt-get install gnome disks
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package disks
james@Bumblebee:~$

---

### Post by sotiris2 on 2014-03-13
You can paste in the terminal by clicking with the mouse wheel. You got a typo (missed -) that's why the last command failed.
So just copy paste the following 

sudo chown -R james:james /media/286ac7f7-c384-4af8-bdf1-5aab0951f491/james 

and execute. 

Then for disks 

sudo apt-get install gnome-disks

and after install 

gnome-disks.

---

### Post by james104 on 2014-03-13
> **sotiris2 said:**
> You can paste in the terminal by clicking with the mouse wheel. You got a typo (missed -) that's why the last command failed.
So just copy paste the following 

sudo chown -R james:james /media/286ac7f7-c384-4af8-bdf1-5aab0951f491/james 

and execute. 

Then for disks 

sudo apt-get install gnome-disks

and after install 

gnome-disks.


Hello

Change ownership has worked perfectly! :)

Now just getting this..

james@Bumblebee:~$ sudo apt-get install gnome-disks
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-disks
james@Bumblebee:~$ 

Is it downloadable another way?

---

### Post by sotiris2 on 2014-03-13
I wanted the tool to have a more graphical approach but it is not necessary

Run on terminal

gksudo gedit /etc/fstab

Authenticate and a text file will come up.
Paste on the last line. 

UUID=286ac7f7-c384-4af8-bdf1-5aab0951f491 /home           ext4    defaults        0       2

Save and close.  Check again filesize of your copy and permissions and if they are identical to the original, delete the original. Rebooting should get you back up with no difference than usual but having more space on your root partition (and avoiding nuisances from that). 

If something does not go well and you can't boot, don't panic and boot from your usb stick and come back from help.

---

### Post by james104 on 2014-03-13
> **sotiris2 said:**
> I wanted the tool to have a more graphical approach but it is not necessary

Run on terminal

gksudo gedit /etc/fstab

Authenticate and a text file will come up.
Paste on the last line. 

UUID=286ac7f7-c384-4af8-bdf1-5aab0951f491 /home           ext4    defaults        0       2

Save and close.  Check again filesize of your copy and permissions and if they are identical to the original, delete the original. Rebooting should get you back up with no difference than usual but having more space on your root partition (and avoiding nuisances from that). 

If something does not go well and you can't boot, don't panic and boot from your usb stick and come back from help.

Thank you, I shall try this evening or perhaps tomorrow morning at around 7am.

I will post my results.

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> I wanted the tool to have a more graphical approach but it is not necessary

Run on terminal

gksudo gedit /etc/fstab

Authenticate and a text file will come up.
Paste on the last line. 

UUID=286ac7f7-c384-4af8-bdf1-5aab0951f491 /home           ext4    defaults        0       2

Save and close.  Check again filesize of your copy and permissions and if they are identical to the original, delete the original. Rebooting should get you back up with no difference than usual but having more space on your root partition (and avoiding nuisances from that). 

If something does not go well and you can't boot, don't panic and boot from your usb stick and come back from help.

Hello

Powered up this morning in preparation to do this and was able to edit the text file. I have since undone that because I found that the 16gb partition had not mounted. When I try to mount it I get a message saying it cant as it requires root!?

I undid my edit of that file just in case the drive should have been mounted first? 

Let me know if I should be concerned or not! 

Thank you! :)

---

### Post by james104 on 2014-03-14
> **james104 said:**
> Hello

Powered up this morning in preparation to do this and was able to edit the text file. I have since undone that because I found that the 16gb partition had not mounted. When I try to mount it I get a message saying it cant as it requires root!?

I undid my edit of that file just in case the drive should have been mounted first? 

Let me know if I should be concerned or not! 

Thank you! :)

Scratch that it is now displaying! Going to try the above now.

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> I wanted the tool to have a more graphical approach but it is not necessary

Run on terminal

gksudo gedit /etc/fstab

Authenticate and a text file will come up.
Paste on the last line. 

UUID=286ac7f7-c384-4af8-bdf1-5aab0951f491 /home           ext4    defaults        0       2

Save and close.  Check again filesize of your copy and permissions and if they are identical to the original, delete the original. Rebooting should get you back up with no difference than usual but having more space on your root partition (and avoiding nuisances from that). 

If something does not go well and you can't boot, don't panic and boot from your usb stick and come back from help.

> **james104 said:**
> Hello

Powered up this morning in preparation to do this and was able to edit the text file. I have since undone that because I found that the 16gb partition had not mounted. When I try to mount it I get a message saying it cant as it requires root!?

I undid my edit of that file just in case the drive should have been mounted first? 

Let me know if I should be concerned or not! 

Thank you! :)

> **james104 said:**
> Scratch that it is now displaying! Going to try the above now.

Ok slightly different query, I am unable to actually delete the default "James" folder. 

Going to edit fstab the file again taking out the line and awaiting your kind advice!

---

### Post by sotiris2 on 2014-03-14
Try doing it from a live usb (be certain to remove the one in the original partition). I am not going to be online till at least 20:00 UTC due to some obligations today. When you have the line in fstab do you boot? If so what does mount (just mount no options no switches no nothing) show? I think it does not mount automatically because a folder with the same name exist in the mount point. Btw better to also remove a folder named 'lost and found' which is in the same folder as your original folder (you may have to 'show hidden files' to see it aka Ctrl+H)

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> Try doing it from a live usb (be certain to remove the one in the original partition). I am not going to be online till at least 20:00 UTC due to some obligations today. When you have the line in fstab do you boot? If so what does mount (just mount no options no switches no nothing) show? I think it does not mount automatically because a folder with the same name exist in the mount point. Btw better to also remove a folder named 'lost and found' which is in the same folder as your original folder (you may have to 'show hidden files' to see it aka Ctrl+H)


Well I put the line into the text file and rebooted and it has still booted fine (phew)

I am unsure as to why it doesnt show the second partition, maybe like you said, once I remove the old original it will mount it automatically ( I hope!) What I see at the top under devices is the 129GB file system and then under computer the folder structure as normal. What I would expect to see is my 16gb one listed a little further down..

I will log on this evening to see if I can complete the process.

Thanks!

---

### Post by james104 on 2014-03-14
> **james104 said:**
> Well I put the line into the text file and rebooted and it has still booted fine (phew)

I am unsure as to why it doesnt show the second partition, maybe like you said, once I remove the old original it will mount it automatically ( I hope!) What I see at the top under devices is the 129GB file system and then under computer the folder structure as normal. What I would expect to see is my 16gb one listed a little further down..

I will log on this evening to see if I can complete the process.

Thanks!

Well I put the code into the fsth file and as you said it didnt mount the 16gb as there were duplicate user folders so I have undone that to allow me to see both again for now.

I booted to a live USB but the delete option was not available.

I shall await your sound advice when you are next free!

Once again thanks!

---

### Post by james104 on 2014-03-14
> **james104 said:**
> Well I put the line into the text file and rebooted and it has still booted fine (phew)

I am unsure as to why it doesnt show the second partition, maybe like you said, once I remove the old original it will mount it automatically ( I hope!) What I see at the top under devices is the 129GB file system and then under computer the folder structure as normal. What I would expect to see is my 16gb one listed a little further down..

I will log on this evening to see if I can complete the process.

Thanks!

Well I put the code into the fsth file and as you said it didnt mount the 16gb as there were duplicate user folders so I have undone that to allow me to see both again for now.

I booted to a live USB but the delete option was not available.

I shall await your sound advice when you are next free!

Once again thanks!

---

### Post by sotiris2 on 2014-03-14
Please give me the result in terminal of the command

```
mount
```

Keep in mind that if it works you will not see something different in the file browser. Your home folder icon wont turn to a disk for example or something like that as in windows, in simple operation a mounted partition and an folder in the actual filesystem/partition do not have any differences. 


In deleting from the live session remember to select the partition and then on /home and delete james, don't be confused with the fact that the live session has it own filesystem with its own /home folder.


If you are certain you are trying to delete the correct folder but it still doesn't let you run 


```
gksudo nautilus 
```

and use that window to delete the folder.

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> Please give me the result in terminal of the command

```
mount
```

Keep in mind that if it works you will not see something different in the file browser. Your home folder icon wont turn to a disk for example or something like that as in windows, in simple operation a mounted partition and an folder in the actual filesystem/partition do not have any differences. 


In deleting from the live session remember to select the partition and then on /home and delete james, don't be confused with the fact that the live session has it own filesystem with its own /home folder.


If you are certain you are trying to delete the correct folder but it still doesn't let you run 


```
gksudo nautilus 
```

and use that window to delete the folder.

Quick recap, I amend the fsah text file then delete the home folder and reboot? :)

Thanks again!

On mobile phone at the mo but hoping to do this soon! Lol

---

### Post by sotiris2 on 2014-03-14
Yes but make sure fstab is correct (copy-paste the entry don't type).

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> Yes but make sure fstab is correct (copy-paste the entry don't type).

Hello,

Mount code

james@Bumblebee:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
james@Bumblebee:~$ 

Upon running nautilus I get a sea of folders but unsure which to remove? or where to go to get to the one to remove?

---

### Post by james104 on 2014-03-14
Hello,

May hae done something daft, removed my folder called James before editing the file and now cannot run anything as root. What shall I do? cannot undo my action!!

---

### Post by sotiris2 on 2014-03-14
Is this on the live session?

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> Is this on the live session?

Hello

This is on my true install not on live usb.... :(

---

### Post by sotiris2 on 2014-03-14
Did you edit the fstab file to include the line before deleting the james folder?  If yes simply restart
If not restart and boot from live cd, and edit it from there. 

From a live cd you will have to find the fstab file of your install and not of the live usb. In order to do so i would suggest again running

gksudo nautilus.

Then looking for the correct partition on the sidebar (you should be able to identify it by size) and in that partition browse to folder *etc*, you will find fstab there, opening normally should allow you to edit and paste that line.

Remember that in live session you still have firefox and can come to this forum.

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> Did you edit the fstab file to include the line before deleting the james folder?  If yes simply restart
If not restart and boot from live cd, and edit it from there. 

From a live cd you will have to find the fstab file of your install and not of the live usb. In order to do so i would suggest again running

gksudo nautilus.

Then looking for the correct partition on the sidebar (you should be able to identify it by size) and in that partition browse to folder *etc*, you will find fstab there, opening normally should allow you to edit and paste that line.

Remember that in live session you still have firefox and can come to this forum.


ok wish me luck!

---

### Post by sotiris2 on 2014-03-14
Something i forgot if you can't boot and have to go to the live session after going to /etc and editing fstab go back up , go to /home, show hidden files (ctrl + H) and delete all files inside home including the one called lost and found

---

### Post by james104 on 2014-03-14
Hello,

I get two locations, one being the memory stick Ive booted to (Live USB) and also the additional mem stick I copied some commands on.

I dont see one the is my proper install and additional partition. Should that be that way?

the fstab file I edit is in the file system location on the left?

---

### Post by sotiris2 on 2014-03-14
Are you in the live session? I presume simply rebooting to disk did not work? 

If in live do you see any hard disk icons in launcher (the vertical bar on the left).

If you can't find it via gui do the following in terminal (one by one)

```
mkdir ./real

mount /dev/sda5 ./real

gksudo gedit ./real/etc/fstab

sudo rm ./real/home/*

ls -a ./.real/home
```

If done correctly the third should open the fstab file you need to put the line in , and the last should show nothing. 

remember the line is 

```
UUID=286ac7f7-c384-4af8-bdf1-5aab0951f491 /home ext4 defaults 0 2
```

---

### Post by james104 on 2014-03-14
Got it, just edited the file that was clearly not on the live usb, the home folder was empty but at one stage (oddly had shown an ubuntu folder)

I am going to restart now and see if I can login..

---

### Post by james104 on 2014-03-14
Got it, just edited the file that was clearly not on the live usb, the  home folder was empty but at one stage (oddly had shown an ubuntu  folder)

I am going to restart now and see if I can login..

---

### Post by james104 on 2014-03-14
OMG!!! I could just kiss you! of course I am not.......

It booted and from what I can see my new 16gb partition is now the new home for my home folder (can you confirm?) 

[IMG]http://i61.tinypic.com/21kwhp0.png[/IMG]

You my friend are a legend! you have given me my first proper insight to Ubuntu and I know I made the right choice to dual boot with this! 

Fingers crossed I wont be running into space issues.

btw where do updates download/install to now? Main partition or the extended/additonal one I created (which is now my home)

---

### Post by sotiris2 on 2014-03-14
disk utility speaks the truth :p

They install on the main partition. 
Steam and it's games however install on your /home folder

You are welcome I am sorry I made some silly mistakes such as not anticipating troubles with deleting your original home folder and not realizing gnome-disks is not a default program wasting a bit of our time.

Now if you ever reinstall (say to get a newer version such as 14.04) simply chose the one that you have as root (/) now to be root again , allowing the installer to format, and the new home partition to be mounted as /home (without formatting) and you 'll keep your files and configurations.

---

### Post by dark_cradle on 2014-03-14
> **Mark Phelps said:**
> Couple of words of caution (from experience:)
1) Do NOT use GParted to shrink down your Win7 OS partition if that is where you end up having to get more space for Ubuntu.  Doing that risks corrupting the Win7 OS filesystem and rendering it unbootable -- making it really hard to fix.

I usually modify Windows partitions with Gparted, and is really difficult to get the Win unbootable. You only need the installation disk, and by clicking "Repair" all boot problems are solved. 100%.

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> disk utility speaks the truth :p

They install on the main partition. 
Steam and it's games however install on your /home folder

You are welcome I am sorry I made some silly mistakes such as not anticipating troubles with deleting your original home folder and not realizing gnome-disks is not a default program wasting a bit of our time.

Now if you ever reinstall (say to get a newer version such as 14.04) simply chose the one that you have as root (/) now to be root again , allowing the installer to format, and the new home partition to be mounted as /home (without formatting) and you 'll keep your files and configurations.

Hah it doesnt lie!

Dont be silly no need to apologise, I have worked with windows for years and as I said I am new to all this but you were fantastic in helping me throughout. most wouldnt have the same patience you had, I just wish I could repay you somehow ( a virtual beer?!) lol

I will look into 14.04 when it crops up, I use Ubuntu primarily for Football Manager as you may have seen and that I believe is only supported on 12.04 which I am happy with so far.

Are there any major differences? Would I simply then just "upgrade" as I would in windows and retain all programs etc then? Interesting!

---

### Post by sotiris2 on 2014-03-14
No need for a virtual one I am sipping a real one right now! :lolflag:

 As for upgrading, I would recommend downloading the iso for the new release and installing freshly but choosing only to format the **/** partition which has the system files while making it mount your existing home partition as home (much easier in the installer i promise!) without checking to format thus keeping your files and some application settings (though you 'll have to reinstall the programs themselves). Steam however keeps games at /home so even though you'd reinstall steam it will probably find fm and not re-download it. Of course first check if steam will work in the newer version! 

It will be supported i believe since 14.04 will be a lts version just as 12.04 is. Nevertheless although 14.04 will be a more current version 12.04 will continue to receive updates up to 2015 so you don't have to worry (in fact even if you plan to update i would suggest to wait a month or so for any release bugs to be squished out)

Is fm performing well under Ubuntu? I would hope so since its one of few games that are actually mostly cpu intensive than graphics-heavy. Been few years since I 've burned some time in it (well buckloads of time). 

Finally you should mark this thread as solved, though I can't help you with that ;)

---

### Post by james104 on 2014-03-14
> **sotiris2 said:**
> No need for a virtual one I am sipping a real one right now! :lolflag:

 As for upgrading, I would recommend downloading the iso for the new release and installing freshly but choosing only to format the **/** partition which has the system files while making it mount your existing home partition as home (much easier in the installer i promise!) without checking to format thus keeping your files and some application settings (though you 'll have to reinstall the programs themselves). Steam however keeps games at /home so even though you'd reinstall steam it will probably find fm and not re-download it. Of course first check if steam will work in the newer version! 

It will be supported i believe since 14.04 will be a lts version just as 12.04 is. Nevertheless although 14.04 will be a more current version 12.04 will continue to receive updates up to 2015 so you don't have to worry (in fact even if you plan to update i would suggest to wait a month or so for any release bugs to be squished out)

Is fm performing well under Ubuntu? I would hope so since its one of few games that are actually mostly cpu intensive than graphics-heavy. Been few years since I 've burned some time in it (well buckloads of time). 

Finally you should mark this thread as solved, though I can't help you with that ;)

Ah ok, ill keep my ear to the ground re that one then, 12.04 is really good and stable. Yes FM runs so much better than on windows, in due course I will remove FM from windows as this was a trial period and has past with flying colours! I wasnt sure what to expect. My old dog of a laptop now runs really well (under ubuntu)

I cant migrate fully as im a new iphone user so ITunes is a regular program for me lol

I will mark this as closed, if there is anyway I can recommend you on this forum I will! I can only hope I gain as much even half the linux knowledge you have Ill be happy!

---

