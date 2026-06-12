---
title: "[SOLVED] Attempting to create a partition for Ubuntu"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Binary.tobis on 2008-06-04
Hi all. I am attempting to install Ubuntu for the first time, I was always curious and thought I would give it a shot. I am trying to install it on an old laptop which already has windows installed. The question I have is whether or not it is possible to create a partition to install Ubuntu on without wiping and reinstalling windows. Is it possible/relatively simple to create a second partition inside of windows? Do I need special programs? I also don't know anything about installing Ubuntu but I figure this is the first step.

---

### Post by Happy_Man on 2008-06-04
The installer on the LiveCD walks you through all the partitioning, don't worry, it's not as bad as everything makes it out to be. I do recommend defragging at least twice before you start to prevent any sort of data corruption/loss.

---

### Post by tamoneya on 2008-06-04
the best way is to install gparted first.  go into terminal (applications -> accessories -> terminal) and type```
sudo apt-get update
sudo apt-get install gparted
sudo gparted
```This should start a GUI interface.  From here you need to take your NTFS(windows) partition and make it smaller.  This will leave space for you to make the ubuntu partition (ext3) since you cannot make it inside the windows partition.  
To make the ubuntu partitions you can just run the installer and tell it to install in the empty space(the space gained by shrinking the ntfs partition).

---

### Post by bumanie on 2008-06-05
Yes, you can install ubuntu without disturbing windows. You can use the partitioner as the sole tool or you can pre-format/partition with gparted. Gparted is on the live ubuntu cd or you can download a dedicated version off the internet. Gparted has a easy to follow gui - when I first started with ubuntu I used the gparted live cd to make sure I had 'isolated' my xp installation. Now I don't touch windows at all. If you need help after having a look at things, post again with specific questions and someone will help.

---

### Post by mdpalow on 2008-06-05
Don't forget to either make a back-up of your disk or at least make sure you have a back-up of your important files.

Would hate for you to be _another_ new user who got confused and lost everything because you accidentally wiped out Windows.

Spoke to someone here once who did exactly that and lost thousands of pictures of his grandchildren. His wife was NOT happy and there were NO copies anywhere!

That was a horrible situation that was completely avoidable. 


Safety first.

---

### Post by Paqman on 2008-06-05
The latest version of Ubuntu also has a new install option called Wubi that means you don't need to do any partitioning at all.

Just pop the LiveCD in while you're in Windows and you can make a virtual hard drive on the Windows partition that you can install Ubuntu on to.

---

### Post by Binary.tobis on 2008-06-05
Thank you guys so much for your help!

> **mdpalow said:**
> Don't forget to either make a back-up of your disk or at least make sure you have a back-up of your important files.

Oh, this is my first attempt so I am using a laptop no one will miss if I screw up and I have to take it out back to put it down.

Would it be possible, theoretically, to delete the windows partition at a later date and expand the linux space?

---

### Post by Paqman on 2008-06-05
> **Binary.tobis said:**
> 
Would it be possible, theoretically, to delete the windows partition at a later date and expand the linux space?

No problem at all. Gparted can do that for you.

---

### Post by Binary.tobis on 2008-06-08
So yesterday and the day before I attempted to install ubuntu on an older laptop, but whichever way I tried to install it locked up at some point. The last thing I tried was wiping the hard drive completely and installing ubuntu fresh but that didn't work either.

Eventually me and my friend put xubuntu on there, but I always thought Linux was low-taxing on the system? Does my computer need to have a certain amount of RAM or something before normal ubuntu installs work? I ran the Memory Test and it came back clean.

---

### Post by Happy_Man on 2008-06-08
Linux is low on the system requirements, but a live session (which is nothing more than an entire desktop/running system completely in RAM) is not. Hence, why you may have seen some locking up. The minimum amount for a live install is 256 MB (though you may hear people say 512). If the laptop has less, then a live install is difficult.

---

### Post by Binary.tobis on 2008-06-09
Ah, that makes sense. Thank you much!

---

