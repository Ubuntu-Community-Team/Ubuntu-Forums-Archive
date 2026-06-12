---
title: "[SOLVED] Hard drive usage doesn't add up"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by laffinet on 2008-09-27
I'm sure there was a thread for this already but I can't find it. Sorry for the (possible) double post.

Here's my problem. I recently ran out of hard drive space, although I was quite sure there should still be plenty. I deleted some stuff and checked how much space is left. gparted tells me that I've got about 38gig left, in a partition that is 125gig with 88gig used (see screenshot 1)

So far so good. But when I check in Nautilus I'm told that the home folder totals 64.x gig with 31.5gig free (screenshot 2). This obviously doesn't add up to 125 gig, so where's the rest ?

And which one is it ? 64.x or 88 ? 38 or 31.5 ?

Nautilus also tells me that some contents is unreadable. Que ?

BTW My trash is empty.

Thanks for any help.

---

### Post by talsemgeest on 2008-09-27
You might have some root trash. Have a look in /root/ for some trash there.

---

### Post by squee on 2008-09-27
Run Disk usuage analyser. It'll tell you where its all gone. I found that mine had gone into thunderbird cashe and deleted files.

---

### Post by laffinet on 2008-09-27
> **talsemgeest said:**
> You might have some root trash. Have a look in /root/ for some trash there.

Nope, nothing there.

---

### Post by drs305 on 2008-09-27
There can be trash located in several different places, and you can't use the space until it's emptied. There is a link in my signature line about Trash, full disks, and how to find it.

You can also use the following command to find large files. There are very few files after an install that are larger than 500MB:
```
sudo find / -name '*' -size +500M

```

You can go to "man find" to see other file size designations.

---

### Post by laffinet on 2008-09-27
> **squee said:**
> Run Disk usuage analyser. It'll tell you where its all gone. I found that mine had gone into thunderbird cashe and deleted files.

Maybe I didn't explain it right. I'm not looking for any files that take up a lot of space, I'm wondering about the inconsistency between gparted and nautilus. 

Gparted tells me my /home has 88gig used, nautilus says 65gig and disk usage analyser now says 68.9gig. Now the difference between nautilus and disk usage analyser might be due to how it's measured (the good old 1024 byte in 1 Kb etc.). But that wouldn't explain the 88vs65/68.9

---

### Post by drs305 on 2008-09-27
> **laffinet said:**
> Maybe I didn't explain it right. I'm not looking for any files that take up a lot of space, I'm wondering about the inconsistency between gparted and nautilus. 

Gparted tells me my /home has 88gig used, nautilus says 65gig and disk usage analyser now says 68.9gig. Now the difference between nautilus and disk usage analyser might be due to how it's measured (the good old 1024 byte in 1 Kb etc.). But that wouldn't explain the 88vs65/68.9

I understand this doesn't account for all of it, but part of the explanation lies in the fact that ubuntu reserves 5% of disk space for system use (such as journaling). Disk Usage Analyzer and/or Nautilus, being part of the system, may receive the information correctly, whereas gparted would just be looking at raw partition data. 

The reserved space can be changed using tune2fs with the -m switch, although generally the default serves most people well.

---

### Post by laffinet on 2008-09-28
> **drs305 said:**
>  There is a link in my signature line about Trash, full disks, and how to find it.


Okay, I followed all the steps and things look a bit more consistent now. However, still slightly off:

Nautilus: 64.8 GB used, 49.0 GB free
df -Th | sort: 69G used, 50G free
Gparted: 70.32 GiB used, 55.29 GiB free

This could be the 5% though. Right ?

BTW, there's a small error in your "trash tutorial". Your code reads:

```
df - Th | sort
``` instead of ```
df -Th | sort
``` (blank before Th). Thought I mention it.

One more thing: how can I prevent the trash building up in those "hard to reach" unusual places ? I found stuff in trash folders I didn't even know existed, how does it get there ?

Thanks everyone.

---

### Post by drs305 on 2008-09-28
> **laffinet said:**
> 
One more thing: how can I prevent the trash building up in those "hard to reach" unusual places ? I found stuff in trash folders I didn't even know existed, how does it get there ?

Trash accumulates in various places for a variety of reasons. Each non-linux partition has it's own trash files. Anytime you delete something from one of these non-linux partitions a trash bin is created if it doesn't already exist. Fortunately these will be included in the desktop trash bin if they are designated by uid (i.e. .Trash-1000).

Of course, if more than one user uses the computer, each user has their own trash bins which are also not normally accessible to other users but still take up disk space. And root maintain's it's own trash bin system.

Why so many? One of the reasons is that linux/ubuntu was designed for multiple users. For security/privacy purposes, separate trash bins means that users will have access only to their own files.

One solution would be to create a simple script using the trash commands you found in the trash link and periodically run it. You could also make a cron job or use anacron to automatically run the script to empty the trash. There is a gui app called "gnome-schedule" that can help create an automated script. The important thing is, just like home life, occasionally you have to get rid of the trash.

Thanks for pointing out the typo in the trash tutorial. I've corrected it.

---

### Post by peacechicken on 2008-09-29
> **drs305 said:**
> You can also use the following command to find large files. There are very few files after an install that are larger than 500MB:
```
sudo find / -name '*' -size +500M

```

I'm having this same problem, the Disk Usage Analyzer says I'm using over 145GB but the home folder is showing less than 18GB. My trash has been emptied. 

I did the search for files over 500MB as suggested and found 13 backup files (using Simple Backups) that may be the culprit -- except when I try to view the backup folder it says I don't have permission. Is there a way I could try to delete files through Terminal?

---

### Post by peacechicken on 2008-09-29
Update: I figured out how to delete the inaccessible backup folder (sudo rm -r), so I deleted all the +500M files and am now back to having over 134GB available, yay!

That wasn't too painful, slightly cryptic, but not too bad...

---

### Post by RavUn on 2008-10-06
I had this issue before and am having it again.  It shows I'm using 35 gigs but when I scan home it shows I'm only using 30 gigs.  The way I fixed it before was I ran the disk usage analyzer as root and it shows all of the files that take up space.  I was able to just sudo rm -rf them and all was well.

Anyone know how to run disk usage analyzer as root?

EDIT: In case anyone wants to know, you run:
```

gksudo baobab
``` to run disk usage analyzer as root.  Go to scan filesystem and it'll show everything that's taking up space.  I've noticed if you have very large files they do not remove without using sudo... I had deleted some large iso files a while ago that were stuck in the trash that I had to sudo rm -rf to remove

---

### Post by Orographic on 2008-10-23
If I use the GUI version of the Disk Usage Analyzer I'm told that I have 580GB instead of 290GB available (Its a 320gb disk) but if I use the command above in terminal I get 290GB. 

I can't quite follow that? :confused:

---

### Post by drs305 on 2008-10-23
> **Orographic said:**
> If I use the GUI version of the Disk Usage Analyzer I'm told that I have 580GB instead of 290GB available (Its a 320gb disk) but if I use the command above in terminal I get 290GB. 

I can't quite follow that? :confused:

Disk Usage Analyzer includes information about gvfs, the *virtual* file system in gnome. It essentially doubles the partition size. To exclude the gvfs information, go to Edit, Preferences and untick gvfs.

---

### Post by Orographic on 2008-10-23
Thankyou very much. This is part of the reason I moved to Ubuntu, the support here is VERY good. I'm really liking Hardy Heron. Its a moderate learning curve but fun indeed.

---

