---
title: "Ubuntu updates and bandwidth"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by madguy888 on 2013-06-16
Hi !

I'm using 11.10 on my dell inspiron n4010, now i want to upgrade my OS.

Currently,  I'm learning to code with ROR.  

I'm using a 3G USB stick as my primary connectivity (costly bandwidth  :( ). If it fails, trouble shooting will be hectic task.



I want to install  12.04 or 13.04, which one will be better for me ? 

I need something stable that doesn't eat my bandwidth, Looking for your valuable advice

Thanks

PS: English is not my primary language

---

### Post by Impavidus on 2013-06-16
As you are still using 11.10 I assume you don't need the bleeding edge software. I suggest you install 12.04, which has long term support, saves you from upgrading to 13.10 within half a year and is pretty stable by now.

---

### Post by madguy888 on 2013-06-18
> **Impavidus said:**
> As you are still using 11.10 I assume you don't need the bleeding edge software. I suggest you install 12.04, which has long term support, saves you from upgrading to 13.10 within half a year and is pretty stable by now.

I downloaded the ISO of Ubuntu 12.04.2 LTS. 

Now, i want to install it. Can i backup my data into a new drive ? 

I don't know how to create new drive ? Here is the screen shot Disk Utility

[IMG]http://img809.imageshack.us/img809/3991/tymx.png[/IMG]

---

### Post by Impavidus on 2013-06-18
In Linux we call the entire device a drive, which can have several partitions on it. Calling partitions drives as well is confusing Windows parlance.

My suggestion is to start using a separate home partition, which is a good idea anyway.
In principle you can boot from the live disk you just downloaded (first burn it, of course), convert your old / partition containing your old /home to a new /home partition (deleting all system files and directories and moving home to the root of the partition), start gparted, shrink your current /dev/sda1 by about 30GB, create a new partition for use as / partition and install, which should keep all your files. I actually did something like that not too long ago. However, shrinking partitions can take a lot of time (40 minutes in my case, a nice opportunity to read a book, so the time is not lost) and to be sure you should make backups on a removable drive or somewhere in the cloud anyway, so the only saving is that you won't have to copy everything back. Depending on the external drives you have available wiping the entire drive and restoring the backups may be more convenient, although theoretically it should be slower if your /home is larger than about 10GB.

In concreto:
You can keep your data in a new partition, but I wouldn't call it a backup as long as it's on the same drive.
You can create and modify partitions using gparted, which is included on your live disk.

BTW, your drive has a few bad sectors. This may be a manufacturing error, in which case you shouldn't worry.

---

### Post by 3rdalbum on 2013-06-18
First things first:

In Disk Utility, check the SMART statistics. Check how many "bad sectors" you have. Disk Utility has a warped idea of what is "a few" bad sectors; I recently encountered a disk with over 200 bad sectors. Once you have more than 50 bad sectors you probably need to back up all your data and put the hard disk into the rubbish bin.

Secondly:

If the SMART statistics shows a low number of bad sectors, like ten or twenty, you're probably okay to proceed. Back up your data to a different disk, not just a different partition, but you probably won't lose any data.

When you boot the Ubuntu 12.04 CD and start running the installer, it will ask how you want to install Ubuntu. One of the options will be "Install side-by-side with Ubuntu 11.10". DON'T choose that. Instead, choose the "Upgrade" option, and remove your 3G USB stick during installation. This will actually do a clean install of Ubuntu, but keep your existing files safe.

If there's no Upgrade option, you can choose "Something Else" and then simply find which partition you currently have Ubuntu 11.10 installed to, select it, click Edit Partition and set the mountpoint to "/". Click Ok and Next to start installing. DO NOT click anything else when you are on the Something Else screen.

---

### Post by newb85 on 2013-06-18
+1 to all the advice given so far.

Also, (a little off-topic) I see you use Cairo-Dock.  Be aware the the old methods for installing CD are obsolete, as it's now in the repositories, and can effortlessly be installed from the Software Center or using apt-get.  It will create a couple new session options at the login screen.  (One with Unity and one without Unity.)

Oh, and given that you have bad sectors, you'll want to back up (to a different drive) religiously for a while, just to make sure they aren't multiplying.

---

