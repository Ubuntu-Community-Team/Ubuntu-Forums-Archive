---
title: "[SOLVED] Which files makes most sense to back-up?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by germanix on 2008-10-06
As I am constantly fiddling with my system, and doing most things wrong (fools rush in where angels fear to thread) and there is no fool like an old fool, I find myself re-installing at least twice a week. I know that one should regularly do a back-up, and I do promise myself that every time the system collapses, and I lose all of my data, by somehow newer got around to it.
I do not have many personal files, what is most annoying is that every time I do a new install, my bookmarks in Firefox are gone, and I have to re-install various additional language packs, dictionaries and spelling checkers in Open Office and in Thunderbird.
It is clear for me that I need to back-up my personal files, the problem however is that I do not know which of the hidden files I need to back-up as well. Can anyone help me by telling me which files one needs to include in the back-up for me not to loose all of the above? and which other files also makes sense to include in the back-up?

---

### Post by halitech on 2008-10-06
you can use something like remastersys to create a complete backup or just simply unhide the hidden files in your home folder and back all of them up

---

### Post by mcduck on 2008-10-06
You could just simply back up the whole home directory. The dotfiles are just small text files and hardly take any disk space at all.

Actually you'd probably want to create a separate /home partition so that you don't need to make a backup at all when reinstaling the system.

---

### Post by germanix on 2008-10-06
I would love to create a separate home partition, and I have tried to do it on numerous occasions, but I never seem to be able to get it right. This has been one of the main reasons that I have to do a re-install so often.

---

### Post by halitech on 2008-10-06
when you are doing the install, do manual partitioning. how big is your hard drive? maybe we can give you some ideas on a good partitioning scheme to use

---

### Post by emobrad on 2008-10-06
To help you on creating a home partion, I would do this. 

[Click]("http://gparted.sourceforge.net/livecd.php") for Gparted live CD

Burn that and run it.

Create a partition with an EXT3 filesystem, non-bootable, and make it a decent size (about 1/4 to 1/2 of your OS partition).

Then in ubuntu open up the partition (Places -> <## GB media>) and allow the authorization

Open your file window so you can see your home partition, and drag and drop on to the partition. It'll back everything up. Or just save it onto a flash drive or DVD or something such as that.

---

### Post by wizard10000 on 2008-10-06
I always put /home on a separate partition and if I'm building a server /var goes on its own partition too - just to make sure a runaway process doesn't fill up the filesystem with logfiles.

My own backup strategy works like this -

I use a cron job to mount the spousal unit's My Documents directory and there's a full-time NFS share on my media server where all the multimedia lives.  I use rsync to back up my /home partition, the /etc directory, the video and audio files on the media server and the spousal unit's My Documents folder at 2am every morning.

I heart rsync  ;)

---

### Post by germanix on 2008-10-06
I tried to copy the complete home file to the USB stick by symply dragging the file from "Home" to the USB Window and get the following error message. Currently there is a file on the USB stick called "lost and found" This appeared there after I formatted the stick to ext3 (I assume it contains a few files that was on there before I formatted) I cannot delete this file as also here I am told I do not have permission?

 ERROR while coppying:The folder "jac" cannot be copied because you do not have permissions to create it in the destination.

---

### Post by halitech on 2008-10-06
sounds like you don't have permission to write to the drive. open a terminal and do this
```
sudo ls -l /{drive location}
```

---

### Post by germanix on 2008-10-06
Do not know how to enter the location. It is on the desktop?
Must I type it as is or must I substitute "drive location" with the actual location? Must it be in those brackets, if yes I cannot figure out how to get to it on my keyboard.

---

### Post by eldragon on 2008-10-06
i would definately backup the home partition, and /etc wouldnt hurt either.. it includes all configuration to your system.

then reinstalling, restoring /etc/ and /home/ and re-installing extra software is all you need.

---

### Post by Therion on 2008-10-06
Download *[Quickstart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11).

Use it's menu and back up your /Home, /, and config files.

Restore them as needed.

*Voila*.






*READ the install instructions!!!

---

### Post by halitech on 2008-10-06
> **germanix said:**
> Do not know how to enter the location. It is on the desktop?

open a terminal and do```
sudo fdisk -l
```then post the results back here

---

### Post by JC Cheloven on 2008-10-06
> **germanix said:**
> ...the problem however is that I do not know which of the hidden files I need to back-up as well. Can anyone help me by telling me which files one needs to include in the back-up for me not to loose all of the above? and which other files also makes sense to include in the back-up?

For the particular purpose of avoiding to reinstall everything from the internet, you could include in your backups this directory:
  /var/cache/apt/archives
It saves all installation files (.deb) that you install using apt-get, aptitude, synaptic, and the like. You can reinstall your packages from there. Also you can have a look on [aptoncd]("http://aptoncd.sourceforge.net/") for the same purpose.

Greetings

---

### Post by germanix on 2008-10-06
Problem solved. Thank you to all who helped.

---

