---
title: "How to Reformat My PC's Only Hard Drive Without an Operating System"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by David_Navratil on 2014-07-14
Last week had Windows 7 on my desktop and worked perfectly.  Then wanted to try Elementary OS in a dual boot with Windows 7.  I messed up the installation and when I would boot up I would see the word"PC" 2 times in the upper left corner of screen, 1 under the other.  It looked like it wanted me to make a selection but no response.  It then took me into Elementary OS which worked fine but I never again could get into windows.  Sat I decided to install Ubuntu since it is the most popular and there is a lot of support for it.  I've tried to install it 8 times now.  I've done a complete install where it would erase Elementary OS and reinstall and also went in and tried to do a manual install where it let me do the partitioning.  I still get those 2 words each time I try to boot up and I think it has something to do with last week dual boot attempt.

I want to do a reformat and delete all partitions on my hard drive but have no operating system at all on it that works!! Help me - David

---

### Post by The Cog on 2014-07-14
In this situation, I would use the installer live CD to wipe the existing partition table and some stuff beyond - parhaps the first 10 magabytes. Boot the Ubuntu installer and at the prompt, choose to try Ubuntu rather than installing. This should bring you to a functioning desktop running entirely in memory.

Launch a command prompt window (perhaps known as a Terminal window - I'm not familiar with the Unity desktop). Run the command 
```
sudo parted -l
```
to get a list of the attached hard disks - almost certainly just **sda** but it's best to check. If you are running from a memory stick, you may also see that listed as a hard drive. Assuming it's sda you want to wipe, use this command to write 10 mebibytes of zeros to the start of the hard disk:
```
sudo dd if=/dev/zero of=/dev/sda bs=1M count=10
```

Then you have a blank partition table to start with.

---

### Post by LastDino on 2014-07-14
It will also help if you told us if you plan to install Windows again and dual boot or this is going to be Ubuntu only thing along with output of the above two commands in Cog's post.

You can bring up the terminal in Ubuntu by pressing CTRL+ALT+T. Then copy paste the commands and then copy paste the output back here.

---

### Post by stalkingwolf on 2014-07-14
i would use gparted on the live disk.  it will tell you exactly how many partitions you have on the drive.  You might have a win recovery partition on there that you will want to keep.  You may not want windows but if you someday sell it the buyer might.

---

