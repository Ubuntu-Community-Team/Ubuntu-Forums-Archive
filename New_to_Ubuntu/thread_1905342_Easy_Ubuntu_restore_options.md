---
title: "Easy Ubuntu restore options?"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by justmott on 2012-01-06
So I installed Ubuntu about a month ago on my VAIO.  I am really happy with the performance and features, however I am having difficulty finding a means of making a recovery system.  I just want to be able to have a bootable recovery option to mitigate a system crash, like recovery disks for WIndows.  Can I just use the Ubuntu Live USB that I used to do the original install??

---

### Post by carranty on 2012-01-06
> **justmott said:**
> Can I just use the Ubuntu Live USB that I used to do the original install??

Some things can be fixed from the ubuntu live cd, but if you seriously mess things up and have to do a fresh install you'll loose all your data.  Creating a separate home partition when your installing Ubuntu can limit this.  

I think what you're looking for is something like remastersys

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Its a program that will basically make a live CD of your system as it is now, so if you have to reinstall you can reinstall the state it was in when the CD was made, rather than starting from scratch.

Having said that, its much more difficult to fatally crash your Ubuntu system (accidentally) than it is in windows - provided you use the sudo command appropriately!

---

### Post by Basher101 on 2012-01-06
> **carranty said:**
> Some things can be fixed from the ubuntu live cd, but if you seriously mess things up and have to do a fresh install you'll loose all your data.  Creating a separate home partition when your installing Ubuntu can limit this.  

I think what you're looking for is something like remastersys

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Its a program that will basically make a live CD of your system as it is now, so if you have to reinstall you can reinstall the state it was in when the CD was made, rather than starting from scratch.

Having said that, its much more difficult to fatally crash your Ubuntu system (accidentally) than it is in windows - provided you use the sudo command appropriately!

+1 for remastersys

i use it myself and must say it is THE best backup application i have yet used. I mean, what backup is an entire image of your whole system, configured and with all applications installed that is also BOOTABLE. Also very great to show others your installation.

regards

p.s. Remastersys has only one fatal limitation: space

why space? because the scripts it uses with ubiquity (the installer program) are set for DVDs. That means your backup cannot be bigger than 4 GB or it will not work. The maximum i was able to back up with remastersys was 18 GB

so a BIG recommendation i can give you is to have only a small partition for ubuntu itself (i use 15 GB) and then store everything else on another partition (music, downloads, etc)

---

### Post by carranty on 2012-01-06
> **Basher101 said:**
> i use it myself and must say it is THE best backup application i have yet used. 

The only slight downside is it has a cap of ~4GB, so you'll have to backup most of your personal files (particularly media files) separately - but 4GB is plenty for pretty much everything else.

---

### Post by Basher101 on 2012-01-06
.

---

### Post by carranty on 2012-01-06
> **Basher101 said:**
> i already explained so...
 you should not overlook what others wrote :D

I don't believe I did, I think you included that in an edit to your initial post (it wasn't there when I wrote the reply). But anyway  I agree its a good program.

---

### Post by Basher101 on 2012-01-06
> **carranty said:**
> I don't believe I did, I think you included that in an edit to your initial post (it wasn't there when I wrote the reply). But anyway  I agree its a good program.

i did indeed edit...i have similar situations when i write a great wall of china long post, and when i click submit somone has posted a link that explains it all :D i will simply delete what i wrote in my previous post..

---

### Post by justmott on 2012-01-06
**So I went to the Remastersys page and read the literature on creating a backup.  The directions on the Remastersys site are a little confusing.**

_**First it says:**_

"At the command line, you simply run "sudo remastersys backup" to make a full system backup,  or "sudo su" to become root and then run "remastersys dist" to make a distributable copy to share with friends.  
   There is a configuration file - /etc/remastersys.conf where you can set things like the name of the livecd/dvd, the live session username, other files to exclude from the cd/dvd, etc."

_**Then it says:**_

"The Remastersys repository needs to be added to your /etc/apt/sources.list
 
 Paste the following into the sources.list:
 
For Gutsy and Earlier - up to version 2.0.11-1
 # Remastersys
 deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/
 

For Hardy and Newer with original grub - version 2.0.12-1 and up
# Remastersys
 deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/

For Karmic with grub2 - version 2.0.13-1 and up
# Remastersys
 deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

 For Lucid and Newer - version 3.0.0-1 and up
 # Remastersys for Lucid and newer
  deb [http://www.remastersys.com/repository](http://www.remastersys.com/repository) lucid/

 Then simply either reload in Synaptic or you can "sudo apt-get update" and install remastersys.

If you prefer, you can directly download the files from the correct folder in [http://www.remastersys.com/repository](http://www.remastersys.com/repository)"


**The first part is straight forward, but this second set of instructions is like staring into the abyss.  I am not sure if I even need to do the second part.  Thanks for your response and patience.**

---

### Post by Basher101 on 2012-01-06
ignore those, install it with the software center and just run it. Worked fine for me on 11.10 and 11.04

---

### Post by justmott on 2012-01-06
Thanks, very much appreciated.

---

### Post by justmott on 2012-01-06
I searched the Software Centre for "Remastersys" & "Remaster Sys" to no avail.  Software Centre says "no items match".

---

### Post by carranty on 2012-01-07
> **justmott said:**
> I searched the Software Centre for "Remastersys" & "Remaster Sys" to no avail.  Software Centre says "no items match".

When you search the software centre for a program your really searching the repositories listed in your /etc/apt/sources.list file.  remastersys isn't in the standard repos (repositories) and so you'll need to add a line into this file to tell the software centre to search the remastersys site for programs also.  This is what the second half of that documentation was explaining.

First you'll need to open a terminal (either Applications -> Accessories -> Terminal if you're using gnome, or if using Unity search the dash for "Terminal") and type

```
gksu gedit /etc/apt/sources.list
```This will bring up a text file.  Now what line you will add to this file depends on the version of Ubuntu you're using.  If your using 10.04 or newer copy and paste this line into the file

```
# Remastersys for Lucid and newer
deb http://www.remastersys.com/repository lucid/
```If you're using an older version let me know, and I'll tell you which line you need to include.

Now save and close gedit. Open Synaptic and click the Reload button at the top left (I'm using 10.04, it may be a little different if you're using a more recent version of Ubuntu).

You should now be able to search for and install remastersys ;)

---

### Post by jerrrys on 2012-01-07
Or you could just clone it

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by justmott on 2012-01-07
Now save and close gedit. Open Synaptic and click the Reload button at the top left (I'm using 10.04, it may be a little different if you're using a more recent version of Ubuntu).

You should now be able to search for and install remastersys ;)[/QUOTE]

Since I am running 11.10 I had to install Synaptic, which seems like essential software anyway.  Thanks for the help everyone.

---

### Post by carranty on 2012-01-07
> **justmott said:**
> 
Since I am running 11.10 I had to install Synaptic, which seems like essential software anyway.  Thanks for the help everyone.

Ah sorry, you could have done it via software centre also (I think) -but so long as its working ;)

Also, please remember to mark the thread as 'Solved' if you're satisfied.

---

### Post by justmott on 2012-01-07
So I installed remastersys and ran the create backup option with a disk in the USB.  RemasterSys runs through a number of procedures and when its done a message appears:  "backup has been created in /home/remastersys/remastersys, it is recommended that you test the backup on a rewritable DVD or a virtual machine".  So I searched the system for /home/remastersys/remastersys and to my displeasure this file does not exist.  So I am back to square one.  Is there an easy way to create a system recovery disk/flash to mitigate a system crash or simply to return to the original Ubuntu install settings?

---

### Post by carranty on 2012-01-07
> **justmott said:**
> So I installed remastersys and ran the create backup option with a disk in the USB.  RemasterSys runs through a number of procedures and when its done a message appears:  "backup has been created in /home/remastersys/remastersys, it is recommended that you test the backup on a rewritable DVD or a virtual machine".  So I searched the system for /home/remastersys/remastersys and to my displeasure this file does not exist.  So I am back to square one.  Is there an easy way to create a system recovery disk/flash to mitigate a system crash or simply to return to the original Ubuntu install settings?

I suspect it is in /home/[yourUserName]/remastersys/.  Can you paste the output of the below terminal commands to the thread

```
ls -l /home
```

```
ls -l ~/remastersys/
```

---

### Post by Basher101 on 2012-01-07
> **justmott said:**
> So I installed remastersys and ran the create backup option with a disk in the USB.  RemasterSys runs through a number of procedures and when its done a message appears:  "backup has been created in /home/remastersys/remastersys, it is recommended that you test the backup on a rewritable DVD or a virtual machine".  So I searched the system for /home/remastersys/remastersys and to my displeasure this file does not exist.  So I am back to square one.  Is there an easy way to create a system recovery disk/flash to mitigate a system crash or simply to return to the original Ubuntu install settings?

did you click "Delete tomporary data" ? this will also delete the created .iso. The deafault name is Custombackup.iso

just re-do the backup and leave it like that and move the backup somewhere else. You can then use the Ubuntu tool in the system settings to make a bootable USB with it.

---

### Post by justmott on 2012-01-07
Basher, I am certain I did not click "delete temporary data".  Remastersys did not give me the option to move the backup, in fact I was never able to locate the backup .iso that it created.  This seems like a very cumbersome process to simply restore a system to original.

---

### Post by Basher101 on 2012-01-07
> **justmott said:**
> Basher, I am certain I did not click "delete temporary data".  Remastersys did not give me the option to move the backup, in fact I was never able to locate the backup .iso that it created.  This seems like a very cumbersome process to simply restore a system to original.

hmm it should create the .iso...take a look at your system monitor, at least 1-2 GB of space must have vanished IF the iso was created. Otherwise try reinstalling remastersys and try again (while keeping an eye on the system monitor)

---

### Post by justmott on 2012-01-07
From what I observed Remastersys did create the .iso.  Remastersys stated that the .iso was located at /home/remastersys/remastersys/ but when I searched I was unable to locate any such location.  I would have thought that when I put the blank DVD in the USB and clicked create backup Remastersys would have automatically burned that backup to the disk.  Am I missing something here?  Why would anyone want to place this backup .iso on their hard drive?  The whole idea is that, if needed the backup .iso will wipe the hard drive back to the original install.

---

### Post by Basher101 on 2012-01-07
> **justmott said:**
> From what I observed Remastersys did create the .iso.  Remastersys stated that the .iso was located at /home/remastersys/remastersys/ but when I searched I was unable to locate any such location.  I would have thought that when I put the blank DVD in the USB and clicked create backup Remastersys would have automatically burned that backup to the disk.  Am I missing something here?  Why would anyone want to place this backup .iso on their hard drive?  The whole idea is that, if needed the backup .iso will wipe the hard drive back to the original install.

nono, the custom.iso does not work that way. Once created and put on a DVD or USB, it is just like any other Ubuntu installation DVD or USB. You can then even repartition your system if desired (make sure you have Gparted installed before making the backup). After you set everything, install as usual...set the mounting points, hit install and it will install like any other distro, only that it has all your settings and programs with it. 

note: beacuse it is a bootable live iso of your whole system, you can also just "try ubuntu" to run all your programs (this way you can make a diagnostic iso to see if somethings wrong with all needed programs)

Maybe your iso is hidden? try pressing Ctrl + H to see hidden files.

---

### Post by justmott on 2012-01-07
Then could I just clear all partitions from BIOS and boot my original Ubuntu Live CDh to achieve the "original install"?

---

### Post by cmcanulty on 2012-01-07
I added the repository but it won't install. It says check Internet connection but I am online and only that won't connect

---

### Post by Basher101 on 2012-01-07
i don't know why you have to add any repositories..when i installed ubuntu it was in the Software center and i did not have to add any repos for that. Try installing remasersys via Synaptic Package manager then (synaptic is not pre-installed in oneiric for whatever reason, its in the Software center)

---

### Post by carranty on 2012-01-07
> **justmott said:**
> From what I observed Remastersys did create the .iso.  Remastersys stated that the .iso was located at /home/remastersys/remastersys/ but when I searched I was unable to locate any such location.  I would have thought that when I put the blank DVD in the USB and clicked create backup Remastersys would have automatically burned that backup to the disk.  Am I missing something here?  Why would anyone want to place this backup .iso on their hard drive?  The whole idea is that, if needed the backup .iso will wipe the hard drive back to the original install.

As Basher has said, it doesn't work that way.  The iso should be stored on your PC, I'm currently making a backup of my own setup using remastersys so I can help you better, I'll get back to you when its finished.  Please paste the output of 
```

ls -l /home/remastersys/remastersys
```though, it'll help me help you.

Also, can you please attach the file /home/remastersys/remastersys/remastersys.log to the thread.

EDIT : A backup is going to take too long on this computer, just attach your log file and I should be able to tell you what's going on........

---

### Post by carranty on 2012-01-07
> **cmcanulty said:**
> I added the repository but it won't install. It says check Internet connection but I am online and only that won't connect

What do you mean by *it *says.  Are you using Synaptic, software centre or apt-get?  Please include the full error message.

---

### Post by matza55 on 2012-01-07
Thanks for that tip! Can be another useful program.

---

### Post by Basher101 on 2012-01-07
> **matza55 said:**
> Thanks for that tip! Can be another useful program.

best backup program in my opinion. I wanna see anyone make a bootable, installable live version of their current install which includes all settings and installed programs.


**_[COLOR="Red"][SIZE="5"]NOTE:[/SIZE][/COLOR]_** I forgot to mention the only weakness of Remastersys, it is space. You cannot back up more than ~ 18 GB (i was not able to do more) with it, because all the .iso s it creates MUST be smaller than 4 GB, otherwise ALL the scripts, which are made for the ubiquity installer, will not work, because ubiquity was designed to only install DVD images (which as you know are never bigger than 4 GB...). Make sure to move your big files before making a backup.

i for myself have ubuntu on a 15 GB partition and store everything else on a 1 TB shared partition (for windows too)

---

### Post by matza55 on 2012-01-07
> **Basher101 said:**
> best backup program in my opinion. I wanna see anyone make a bootable, installable live version of their current install which includes all settings and installed programs.


**_[COLOR="Red"][SIZE="5"]NOTE:[/SIZE][/COLOR]_** I forgot to mention the only weakness of Remastersys, it is space. You cannot back up more than ~ 18 GB (i was not able to do more) with it, because all the .iso s it creates MUST be smaller than 4 GB, otherwise ALL the scripts, which are made for the ubiquity installer, will not work, because ubiquity was designed to only install DVD images (which as you know are never bigger than 4 GB...). Make sure to move your big files before making a backup.

i for myself have ubuntu on a 15 GB partition and store everything else on a 1 TB shared partition (for windows too)

But how after fix the /etc/apt?

---

### Post by Basher101 on 2012-01-07
> **matza55 said:**
> But how after fix the /etc/apt?

huh?? :confused:

---

### Post by carranty on 2012-01-07
> **Basher101 said:**
> huh?? :confused:

My thoughts exactly! ;)

---

### Post by justmott on 2012-01-07
Ok, back to the original question.  It seems that Remastersys is not really what I was looking for (I am not concerned with backing up from a specific point in time, or having all of the programs I have installed after the fact as part of the backup, I just want a simple means of returning to the original Ubuntu install state).  That being said: Could I just clear all partitions from BIOS and boot/install my original Ubuntu Live CD to return to the "original install" state?

As a side question, when I want to update my Ubuntu distribution, will it only update changes that have been made to the OS?  Or is it a complete update of the entire OS?

Thanks for all the help.

---

### Post by carranty on 2012-01-07
Well if you want a completely fresh install 'state' without any of your own files, applications or customisations then yeah, obviously a fresh install will do that - but that isn't a backup by any definition.  Is that what you're asking? 

> 
Could I just clear all partitions from BIOS


Is that even possible?  I've never created/altered partitions from BIOS before.  Regardless you can create/modify any partitions during the install process from the live CD, no need to do anything in BIOS.

---

### Post by Basher101 on 2012-01-07
> **carranty said:**
> Well if you want a completely fresh install 'state' without any of your own files, applications or customisations then yeah, obviously a fresh install will do that - but that isn't a backup by any definition.  Is that what you're asking? 



Is that even possible?  I've never created/altered partitions from BIOS before.  Regardless you can create/modify any partitions during the install process from the live CD, no need to do anything in BIOS.

you cannot change partitions in BIOS... you must remove all your partitions from a Live CD boot,

 and yes if you want the "original" state, a normal live cd install will do the job.

---

