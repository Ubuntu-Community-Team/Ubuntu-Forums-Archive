---
title: "HOWTO move /home to a new hard drive"
date: 2006-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by adds2one on 2006-09-03
This HOWTO describes how to move your current /home partition to a new hard drive if you already have /home as its own partition.

I will use my situation as an example but you should be able to adapt this HOWTO to your own situation.

I had a 20GB hard drive with three partitions, /, SWAP and /home.

I had a 150GB hard drive with one partition on it from another computer. I had two folders of data on this drive one called Music and another called Videos.

I physically installed the drive and then restarted the computer.

***************************************************************************
You may have a new drive without any partitions or data on it. If this is the case then after you have physically installed the drive boot up using the Live CD and open a terminal. Use gparted to create a new partition on your new drive. You start gparted by typing this in a terminal *sudo gparted*

You will have to select your new drive from the top right hand side of the screen. gparted is pretty straight forward. If you have any trouble with creating a partition in gparted I am sure a quick search of the internet will give you a wealth of information.
***************************************************************************

So continuing with this HOWTO I opened a terminal and created a mount point:

```
$sudo mkdir /media/newhome
```

I then edited /etc/fstab to include the line:

```
/dev/hdb1 /media/newhome ext3 defaults 0 0
```

You will need to replace hdb1 with whatever drive label and partition you have.

Reboot and you should see newdrive on your desktop. Now is the most important step, we need to copy ALL of the contents of /home onto the new drive. Type this exactly:

```
$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /media/newhome/
```

These commands are important to copy all of the hidden files, hard links and sym links. This command may take a while to run.

We are almost there. :)

Now edit /etc/fstab again, this time uncomment out your old /home by putting a # at the start of the line.

Now edit the line for your new drive to mount it to /home, here is mine:

```
/dev/hdb1 /home ext3 defaults 0 2
```

Save this and restart.

Your /home is now on your new drive. I then moved my Music and Video folders into the /home/username folder.

The last thing I did was to resize my / partition to use the rest of my 20GB drive. To do this I booted up using the Live CD and ran gparted again. I deleted the old /home partition and then moved my SWAP to one end of the drive. I then resized / to fill the rest of the 20GB.

Thats it. :D 

I hope this HOWTO was useful. If you have any questions please ask and I will do my best to help.

---

### Post by andylawrence on 2006-09-04
Wouldn't it be simpler to just use rsync.  To get all hidden files and maintain permissions you could just use the command:

rsync -avP /target_directory /destination_directory

---

### Post by adds2one on 2006-09-04
> **andylawrence said:**
> Wouldn't it be simpler to just use rsync.  To get all hidden files and maintain permissions you could just use the command:

rsync -avP /target_directory /destination_directory

That may be true, and may be easier. I am still relatively new to Linux and the method used in this HOWTO was just the info I found that allowed me to do this.:)

---

### Post by Koybe on 2006-09-05
I can confirm, I made it with rsync as you said and it worked well. :D

---

### Post by heinkel_111 on 2006-09-09
> **andylawrence said:**
> Wouldn't it be simpler to just use rsync.  To get all hidden files and maintain permissions you could just use the command:

rsync -avP /target_directory /destination_directory

Hi, I have gone through this a couple of times, and i will say rsync just appears to be more stable and robust than the find -> cpio pipe method.

I use some different option switches, though:
```
rsync -aS /target_directory /destination_directory
```

I admit the verbose mode -v may be nice in case of something going wrong, but i haven't had then need for it yet.

The -P option, what does it really improve? Are partially transferred files that important, wouldn't you just keep trying until all of it is transferred before you delete?

---

### Post by SevenNinety on 2008-03-05
I tried this, and it worked fine - except it copied all files, even from mounted file systems.  Would -x (one-file-system) work so it only copies from the actual disk and not from mounted file systems?

---

### Post by das letzte einhorn on 2008-05-29
The contents of my home folder are already on another disc. However I had to reinstall Ubuntu a few times, therefore the contents are isolated on my second hard drive. In that case, wouldn't I only have to edit fstab?

---

### Post by pedrogent on 2008-06-27
Thanks a lot for this helpful guide.

:)

---

### Post by Ekeluo on 2009-07-15
This thread is old but, a question: I have a laptop with ubuntu all configured to my liking and running fine. I want to buy a new one. Is it in any way possible (ANY at all) to move this config i.e. my home folder, along with all my files straight to the new one, similar to the steps above?

---

### Post by Chonnawonga on 2009-07-15
Interesting question. You could try using Unison: it can handle connections over SSH connections. I do that to keep my documents synced across my laptop and desktop.

---

### Post by heinkel_111 on 2009-07-15
If what Ekuelo wants to do is to move his files to a new machine *once*, then unison is overkill and the method suggested using rsync will copy the files. You need to have a working network and configure the computers to connect to each other first. As far as I know, unison is more for maintaining two directories (presumably on different machines) in a synchronized state (ie... repeatedly synchronizing files in two directions). 

As for the ssh connection, rsync handles that too.

---

### Post by Ekeluo on 2009-07-16
Thanks for the suggestions, guys (ladies?!)

What I want to do is move as much of my system as possible without really breaking anything. I know I can move the home folder (should be able to do this with back in time [[http://backintime.le-web.org]](http://backintime.le-web.org]) and my trusty simpletech external hdd), but not quite sure which files coming from / will ruin my day. Also are there likely to be any permission issues? I plan to use the no-format-home-directory option upon installing on the new notebook. I think transfer of deb packages from /var/cache/apt/archives is doable, but what else. I have kde 4 and want all my plasma widgets (gotten via 'add hot new stuff') to come with me. Solutions?

---

### Post by hawthornso23 on 2009-07-18
Seems simple enough ... the new drive is mounted under a temporary name - the contents of /home are copied to the new drive - the fstab is then changed to mount the new drive as /home.

NAIVE QUESTION: What happens to the copy of the stuff in old /home. That material is now disconnected from the file system. Is that space recovered automatically? Are the files there deleted? Do they show up in lost+found? If fstab was reverted would those contents still be there"? Are any extra steps required to reuse that disk space for another purpose?

---

### Post by carlodrengen on 2009-08-08
heemm i try to change /etc/fstab file with text editor
needles to say it dittent let me do that

text edit say 
------------------------------------------------------------------------
Could not save the file /etc/fstab.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
------------------------------------------------------------------------
i am root on this machin
plz tell then nube what to do .-)
and how to do it (again with the nube)

---

### Post by drs305 on 2009-08-08
> **carlodrengen said:**
> heemm i try to change /etc/fstab file with text editor
needles to say it dittent let me do that

text edit say 
------------------------------------------------------------------------
Could not save the file /etc/fstab.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
------------------------------------------------------------------------
i am root on this machin  plz tell then nube what to do .-)  and how to do it (again with the nube)


Welcome to Ubuntu and the Ubuntu forums arlodrengen,

Open the file with root privileges by using this command. It will then let you edit and save the changes:
```

gksudo gedit /etc/fstab

```

---

### Post by carlodrengen on 2009-08-08
root@dhcppc3:~# gksudo gedit /etc/fstab

(gksudo:7592): Gtk-WARNING **: cannot open display: 
root@dhcppc3:~# /dev/sdb1 /media/newhome ext3 defaults 0 0
-----------------------------------------------------------------------------------------
is what i got out of that

---

