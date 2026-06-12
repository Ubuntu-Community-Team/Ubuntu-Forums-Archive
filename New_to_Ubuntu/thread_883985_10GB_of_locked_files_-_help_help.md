---
title: "10GB of locked files - help help"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Jay Car on 2008-08-08
Problem:

Files I've copied from several old backup CDs to my desktop cannot be used, moved, deleted, or edited.  I can look at 'em, but not use them in any way.  

I have tried just right-clicking and selecting the "permissions" option with mixed success.  Sometimes it works, sometimes not.  Sometimes I can get files inside a folder unlocked but the folder itself remains locked and undelete-able.  This is not just a case of one folder containing a few files, it's about 10GB worth of folders, each containing several hundred files of varying sorts.  If I have to change permissions on each one, one at a time, I'll never get finished.  

I tried using Alt-F2
gksudo nautilus

But all of the locked files are on my desktop (and can't be moved), and the nautilus utility showed the desktop as being "empty."  I don't understand why.  

I Google-searched using the terms "unlocking files, ubuntu hardy" - "changing permissions on locked files, ubuntu hardy" - "unlocking files copied from CD" - which generally brought up posts from Ubuntu forums, but many of the posts had to do with unlocking system files, which I don't want to do, or the posts were old (2995 to 2006) and the instructions confusing, I used a few of them but didn't really understand what I was doing...(I know, that's taking unnecessary risks, but I need these files to be usable pretty fast, I have a work deadline looming).  

In a pinch I could easily fire up the old win2k machine and copy all those old CD files over there, but I really don't want to do that unless there's absolutely no other way, I'd much prefer to learn how to do things without Windows training wheels. Plus, even if I did that, I'd still have 10GB of files on my Ubuntu desktop that can't be deleted (I get error messages if I try). 

There surely must be an easy way to unlock non-system, user-generated files in Ubuntu. Please help if you can.  Suggestions would be very appreciated.  I am feeling particularly stupid right now for not being able to figure this out.

---

### Post by Jay Car on 2008-08-08
Oops...typo alert.  I accidently wrote "2995" in my original post instead of 2005...(newbees should use preview :)

---

### Post by hrod beraht on 2008-08-08
> **Jay Car said:**
> I tried using Alt-F2
gksudo nautilus

Which is probably getting you to **/root/Desktop**.
Is the Desktop folder empty because you are looking there rather than **/home/jay/Desktop**?

Bob

---

### Post by decoherence on 2008-08-08
> **Jay Car said:**
> 

I tried using Alt-F2
gksudo nautilus

But all of the locked files are on my desktop (and can't be moved), and the nautilus utility showed the desktop as being "empty."  I don't understand why.  



Hrm. Perhaps it no longer thinks you are 'you.'

In this nautilus window, try navigating to /home/yourUsername/Desktop ... start by opening "Filesystem" in the left-hand area.

do you see anything then?

---

### Post by Elfy on 2008-08-08
> But all of the locked files are on my desktop (and can't be moved), and the nautilus utility showed the desktop as being "empty." I don't understand why.

Because roots desktop was empty - go to filesystem, /home/ yopur user and then your desktop - you should be able to change the permissions from there.

The best way would be to chwon the folders to your user but I get a bit confused :)

I'll be back

---

### Post by WRDN on 2008-08-08
In the Terminal, use the "cd" command to change to the directory with the 'locked files'. Then, type:

```
chmod 777 *
```

This will add read, write and execute permissions to all of the files.

If you want to ensure only you can read, write and execute, then replace 777 with 700. Use the number 744 to set the permissions so you can read, write and execute, and all other users can read. Finally, set the permissions to 444 to set the file(s) as read only.

You should also use the "chown" command to change the owner of the file(s).
To do this, use the command:

```
sudo chown -R [username] [directory]
```

---

### Post by Thingymebob on 2008-08-08
> **forestpixie said:**
> 
The best way would be to chwon the folders to your user but I get a bit confused :)

I'll be back
thats what id do, chown to me from the terminal
```

cd Desktop
sudo chown jay *

```

---

### Post by Jay Car on 2008-08-08
Wow!  I barely had time to grab a cup of coffee and refresh the page!  Thanks for all your suggestions.  I'll report back asap.

---

### Post by InfinityCircuit on 2008-08-08
It may also be a user mismatch problem. If you post the output of ls -l $HOME/Desktop, it will be easier to diagnose.

---

### Post by Elfy on 2008-08-08
> **Thingymebob said:**
> thats what id do, chown to me from the terminal
```

cd Desktop
sudo chown jay *

```

Yea that thing there :)

sudo chown user.users /mount/point

---

### Post by Jay Car on 2008-08-08
When I do the Alt+F2 and "gksudo nautilus" the tree on the left shows:
>Home Folder
when expanded it also shows Desktop, but expanding the desktop only shows the word (empty).
my user name is not there.

The next item in the tree is File System, and when expanded I do see a "usr" folder, but I don't see anything in it that seems to be my desktop, my user name doesn't show anywhere (I didn't dig through every folder though).

Next I did this suggestion: 
cd Desktop sudo chown jay *

And it worked on all of the files inside the folders!!  Yaay!
However, the folders themselves still have locks on them. 
How do I indicate that the folders, as well as the files inside should be unlocked?

One more question (if I may).  I had planned to take Win2k off of my old computer and try Ubuntu on it, but first I wanted to make sure I had everything backed up.  Having suffered more than one hard drive failure this last year I was running short of storage space, so I purchased a second internal drive for my Ubuntu machine.  It's a 250GB Seagate SATA drive.  The new drive does show up on my computer's list of drives, but nothing (so far) has worked to allow access to it.  It keeps telling me I don't have permission.  I really really really need that storage space.

My new computer came with Ubuntu installed, so it's never known Windows.  I love this computer, and have been blown away at how much easier it has been to use than I ever expected.  I'll never go back. But the problems I seem to have most consistently are "permission" problems.  I receive work files from a lot of different people, running lots of different types of computers.  I rarely have problems doing that, but sometimes I am refused permission to access a file for no apparent reason. Generally, because most things come in by email, I'll just re-download the files to my win2k computer.  But I'd really like to stop doing that.  

Is there some recommended reading to help me understand the file system better? 

I'd say the issue of not being able to easily gain the use of important files and folders (I don't mean system files) and new hardware, when necessary, is the biggest frustration I've faced during my transition away from Windows.

I really hate it when my computer bosses me around and forgets my name :)

---

### Post by Elfy on 2008-08-08
You should see similar to this screenshot in root nautilus.

As far as the new drive goes - assuming it is ext3

Make a new folder - change name to suit - make it the same name in fstab.

```
sudo mkdir /media/*foldername*
```

Get the UUID for the drive to use in fstab

```
sudo blkid
```

Backup and edit fstab

```
sudo nano -B /etc/fstab
```

Add these lines at the end - change new drive to suit

```
#new drive
UUID=*numberyougetfromblkid* /media/*foldername* ext3 defaults 0 2
```

Close and save - Ctrl+O, Enter, Ctrl+X

See if drive has mounted ok 

```
sudo mount -a
```

---

### Post by Jay Car on 2008-08-08
> You should also use the "chown" command to change the owner of the file(s).
To do this, use the command:

Code:

sudo chown -R [username] [directory]

WRDN,

Would the name I put in as the directory be "desktop" and should the brackets be kept? 

Could that also be used to gain access to my new hard drive?

---

### Post by Thingymebob on 2008-08-08
> **Jay Car said:**
> WRDN,

Would the name I put in as the directory be "desktop" and should the brackets be kept? 

Could that also be used to gain access to my new hard drive?

the directory part is optional, if you omit it it will work from the current directory down don't add the brackets

---

### Post by Jay Car on 2008-08-08
> As far as the new drive goes - assuming it is ext3

Forestpixie, I don't know if it is ext3.  It's brand new, so I'm assuming that it's NTFS, if it's formatted at all.  How do I find out?  When I select "Properties" for the drive it just lists everything as "unknown".

---

### Post by Jay Car on 2008-08-08
Almost forgot...

I did find the locked folders in Nautilus, under File System >Home >MyUserName >Desktop.  I have ALL the files and folders unlocked now!  

Thank you all VERY much for helping with that. Yaay!

Now I'm going to get that new hard drive working.
:)

---

### Post by Jay Car on 2008-08-08
> It may also be a user mismatch problem. If you post the output of ls -l $HOME/Desktop, it will be easier to diagnose.

Infinitycircuit,

I did run that line, but the resulting output is very long and lists names of files and folders on my desktop (of which there are many right now) with a great deal of personal information in the file names, so it's probably best if I don't post it here.

Mine is the only user name on the machine.

---

### Post by WRDN on 2008-08-08
> **Jay Car said:**
> WRDN,

Would the name I put in as the directory be "desktop" and should the brackets be kept? 

Could that also be used to gain access to my new hard drive?

If you wanted to change the owner for the Desktop directory, you would type:

```
sudo chown -R [username] ~/Desktop
```

Generally, it is best to use "~/Desktop" rather than "/home/[username]/Desktop" because it ensures the command is as portable as possible.

---

### Post by Jay Car on 2008-08-08
Forestpixie,

I copied your instructions and read them through several times.  I thought it might be good to disconnect any extra hard drives from my computer before I start working to get the new drive set up, so I did that first.

I'm afraid I just didn't understand the steps you gave me. Not sure what I did wrong, but I worked at it for quite a while. The new hard drive is still unaccessable.  I was never able to get the UUID. 

So I did some more searching. The difficult part of searching for info about hard drives is that so many posts that show up in the search have to do with dual-booting, or using gparted to allow Ubuntu to install on the same drive with Windows. I just want to add a brand new slave drive to my Ubuntu machine.

I did run across this tutorial:
[http://www.techotopia.com/index.php/Adding_a_New_Disk_Drive_to_an_Ubuntu_Linux_System](http://www.techotopia.com/index.php/Adding_a_New_Disk_Drive_to_an_Ubuntu_Linux_System)

I followed it very carefully, and every step worked exactly the same on my machine as it showed in the tutorial (except for the different drive size), until I reached this part:

> **Now that we have specified the partition we need to write it to the disk using the w command:**

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

When I typed "w" the "partition table has been altered!...etc" text didn't show up.  I should have kept a copy of that session, I'm sorry.  It would be easier to explain if I had. The drive was still not accessable though.

Then it hit me that many of the posts I'd found about hard drives mentioned gparted. Even though few of those posts were actually about adding a brand new drive, I thought it might be a solution. So I fetched it from the repository and ran it, but gparted didn't "see" my new hard drive at all...though the drive does still show up in my Places >Computer list.

Maybe it's just a bad drive.

I think I'm too tired to do more tonight, but I'll try to go back over everything tomorrow.  

Anyway, thanks to everyone for their help. Ubuntu forums are great and so are the people that help us struggling newbees out.

Jay Car

---

