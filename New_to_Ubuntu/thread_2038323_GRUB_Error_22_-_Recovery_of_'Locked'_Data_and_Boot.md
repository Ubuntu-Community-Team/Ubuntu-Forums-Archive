---
title: "GRUB Error 22 - Recovery of 'Locked' Data and Boot Repair"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by zeesh1989 on 2012-08-06
Hey there everyone!

This is literally my first post here at the Ubuntu forums - so please go easy on me.
[B]
Background on the issue:[/B]
I  have had Ubuntu 9.10 installed on my desktop computer and it was giving  me issues with updates - it kept on showing that your 'release is no  longer supported' and asked me to upgrade to a newer version of Ubuntu.  This however wasn't possible for some reason or another - as kept on  showing an error in the middle of the upgrade.

This combine with  the fact that I couldn't get my wireless dongle working with Ubuntu any  more I decided to finally get my data backed up and then formatted at  the local computer shop and try and get install windows first (and  Ubuntu with it at a later date).

Until the time that I gave the  computer to the shop the OS at least loaded up fine. But after he tried  to recover the data separately from hard drive itself I have started to  have the following issue.
[B]
The meat of the problem:[/B]
After starting up the PC (with the (internal) hard drive connected back appropriately) the screen shows the error:
'GRUB loading stage1.5

GRUB loading, please wait

ERROR 22'

So after my research I found that the first thing to do is to boot via a Live CD/USB.
I  managed to boot up (using a Live USB) the latest version of Ubuntu  Desktop (12.04 LTS) and then selected the 'try Ubuntu' option.

This  takes me to the desktop to 'try' the OS out. After this when I opened  up the 'Home' folder - where I found my hard drive on the top left  (named 631 GB something something). I clicked it to mount the hard drive  after which all my data was there. However, most of it had a lock on  the logo of it - so when I tried to copy the data to my external hard  drive the system would prompt (something along the lines of) 'the folder  cannot be handled because you do not have permissions to read it'.
Hence, I am unable to copy all of my data on to my external hard drive.

Therefore,  on advice of what most forums suggest on boot issues I tried the Boot  repair - via a connection to the internet. The first time I tried the  'Recommended repair' it prompted me with some codes to past in the  terminal - basically manually making me remove (or 'purge') GRUB and  then try to re-install GRUB2 - but there was an error in the terminal  basically stating that GRUB2 couldn't be downloaded from the repository.
I noted the URL it gave me - [http://paste.ubuntu.com/1130935](http://paste.ubuntu.com/1130935)

After this I tried Boot repair again this time after scanning my system it showed me the following error:
'Add repository containing grub2 packages in software sources in ubuntu 9.10'
After this it shows the software center options at which point I have no clue as to where to go forward.
The URL that it gave me after this error was  - [http://paste.ubuntu.com/1130995](http://paste.ubuntu.com/1130995)
[B]
Objective:[/B]
I  am just using boot repair as a last resort. Honestly speaking if there  is any way to just recover all of my data completely - by copying and  pasting it on to my external hard drive - I would be more than pleased  with that outcome. As I intend to format the internal hard drive anyway.
So  if someone could just suggest as to how to remove the locks off my data  via the Live USB (of Ubuntu Desktop) that would be more than enough.
[B]
Other options:[/B]
However,  as a last resort my other options are Boot Repair (issues stated  above), TestDisk (no idea as to how it works and how it would paste my  data on to my external hard drive), Ubuntu Rescue Remix (another form of  TestDisk), or Rescutux and/or Super GRUB2 (from  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)). I don't have much of a clue as to how  any of these softwares operate. :confused:

**Any help would be highly appreciated. **:smile:
Thanks in advance.

---

### Post by audiomick on 2012-08-06
To copy your files off, try using an instance of Nautilus with root privileges from the live CD.

In a terminal

```
gksudo nautilus
```

whilst booted into the live environment. The file manager that then starts has root privileges, and should be able to access everything.

What you have to watch out for is that, as far as I know, the owner of the copied files will be root if they are copied to a Linux file system. If the external has, however, a windows file system such as FAT32 or NTFS, I don't think this is an issue, as those file systems don't support Linux permissions.


As far as the boot repair goes, my first guess would be that the boot repair environment is not getting an internet connection, but that is really just a guess.

---

### Post by NikTh on 2012-08-06
Hi , 
copy your important data to another disk (or partition) with command @audiomick suggested. 

Do a fresh installation of Ubuntu. Install a supported version. If you want help with what version must install to meet your computers hardware , give little more information about computer's specification.
eg 

> model 
Cpu 
Gpu (graphics card)
HDD 
RAM and you will have lot of suggestions about what version of Ubuntu will fit better to your computer.

Thanks

---

### Post by zeesh1989 on 2012-08-06
@audiomick

Thanks for your quick reply!

I tried using an instance of Nautilus with root privileges from the live CD and the terminal opened up a file manager which allowed me access to everything.

However, when I am copying the files some are still giving me the same error of 'permission to read it'.

I am currently copying all that I can but prefer to have the rest of the data as well - any idea how I could sort it out?

Regarding the Boot Repair - I had it connected to a wired connection and even checked the internet via Firefox. So not sure if it's an internet issue.

Really appreciate your help!

@NikTh

I will post the details as soon as the data has been backed up.
Would appreciate your help with the recommendations. However, do you think I could install windows first and run ubuntu as a dual boot? Or would that pose long term problems? I read that this GRUB Error 22 is famous with dual boot issues. 

Thanks for your help!
[]("http://ubuntuforums.org/member.php?u=1566509")

---

### Post by oldfred on 2012-08-06
Grub error 22 is from grub legacy. You must have upgraded from 9.04 to 9.10 as 9.10 was the first to use grub2 as default, but still used grub legacy from upgrades.

Boot Repair only works with grub2, and since 9.10 is not supported, it cannot download grub2  from the repositories as they are now closed.

Script is not showing menu.lst & boot files in your sda1, so you do need repairs to make it work, but better to backup data and/or all of /home and install a newer version that is still supported.

Only if you still have liveCD from 9.10 may this work.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by audiomick on 2012-08-06
> **zeesh1989 said:**
> @audiomick
However, when I am copying the files some are still giving me the same error of 'permission to read it'.

I am currently copying all that I can but prefer to have the rest of the data as well - any idea how I could sort it out?

hmmm, that is a tough one for me. I'd have to be looking at the computer myself. You could try looking at the properties of the things you can't copy (right click on the file). Maybe that would yield some useful information.

---

### Post by zeesh1989 on 2012-08-07
> **audiomick said:**
> hmmm, that is a tough one for me. I'd have to be looking at the computer myself. You could try looking at the properties of the things you can't copy (right click on the file). Maybe that would yield some useful information.

@audiomick

I just had another go at it and its copying all the files just fine this time!
What I was doing wrong (stupidly in hindsight) was that I selected my External Hard drive separately - from the 'Home' icon on the left.
Now that I selected both the hard drives from the file manager that opens from the terminal, no such error appears.

Thanks so much for your help.
I will post the details of the computer once I have everything sorted.

---

### Post by audiomick on 2012-08-07
Great. Glad it is working out.

---

### Post by zeesh1989 on 2012-08-11
Any idea as to how I can change this thread to 'SOLVED'?

---

