---
title: "Out of space error when I have 700 gigs left"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by willis11of12 on 2012-04-09
I am getting an out of space error and can't run my apps, but when I look, I see that my home folder is only using about 200+ gigs, with 700+ gigs left free on the HDD.  Am I only allowed to have so much in the home folder and need to move some of this stuff into another folder in the file system?  I tried to transfer some over, thinking that may be the solution, but it won't let me do that.  Do I need to sing in to administrator for that?  What is the real problem here and what is the proper solution?  Thanks!  :)

---

### Post by oldfred on 2012-04-09
How big is / (root) partition?

sudo df -H

---

### Post by lukeiamyourfather on 2012-04-09
The home folder might be on a partition by itself. Try this command to see how much space each mount has.

```
df -h
```

---

### Post by drs305 on 2012-04-09
*willis11of12*

Welcome to the Ubuntu Forums.

Sorry you are having disk space issues. You can take a look at the following thread which gives a combination of terminal commands and GUI apps to help you investigate the problem.
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

The three things that consistently cause problems (assuming the partition is actually of sufficient size for a normal installation) are accumulated Trash (trash continues to take up space until the Trash bin is emptied - your's and the administrator's/root's), backups which were made to the wrong partition, and large log files.

Methods for dealing with these are also addressed in the link.

If the guide is too advanced, just come back and ask for more help.

---

### Post by willis11of12 on 2012-06-20
Sorry for the delayed response!  Here is what I currently see when using "df -h":

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       920G  290G  584G  34% /
udev            5.6G  4.0K  5.6G   1% /dev
tmpfs           2.3G  876K  2.3G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            5.7G  704K  5.7G   1% /run/shm

I am not currently having the problem since I transfered the large files I had from a folder in my home folder to an folder in the system drive folder.  I'm guessing that there is some kind of limit on how much data can be in my home folder?  I don't recall setting this up, so I am guessing there is some default setting.  If so, where can I find this setting and change it, or can I only do that when I am setting up and partitioning the hard drive?  

In any case, I am not having the problem after I move files to the file system, so that is my work around for now, to just move them over when it starts getting too big in the home folder.

Thanks for the replies!  :)

---

### Post by dFlyer on 2012-06-20
I'm confused, your only running one linux partition with both root and home in the same partition. Your home folder size shouldn't matter just as long as you have used only 34% of the linux partition. When you say you move some large files where did you move them to?

---

### Post by willis11of12 on 2012-06-22
> **dFlyer said:**
> I'm confused, your only running one linux partition with both root and home in the same partition. Your home folder size shouldn't matter just as long as you have used only 34% of the linux partition. When you say you move some large files where did you move them to?

Yeah, it makes no sense to me why this was the case from looking at it, but for some reason that is what happened and what I had to do to fix it.  I had applications running that were collecting number feeds into files and they were building up in a folder that was inside of my home folder and once the home folder was about 200 Gigs I think it was, it said I was out of space and I could barely function, and the data files apparently couldn't fit any of the additional data that was trying to come in.  I couldn't start gathering the data again until after I moved most of the files out of that folder and into a folder in the file system.  After that, the applications were able to start gathering the data again.  I don't know why I should have had to do that, as it looks like it's all the same partition anyway, but that's what happened.  It was quite the headache last time, so hopefully I'll remember to transfer the files again before it gets to that point again, or find a way to change whatever setting is causing the problem...  but I don't know where to look!  lol

So in short, I moved the files from a folder in my home folder to a new folder in the file system and then things worked fine again...  For now.  :)

---

### Post by willis11of12 on 2012-06-22
I don't know if this makes a difference, but this problem happened when I was using an earlier version (11.10 I think?) and now I am using 12.04 LTS.  I'm not sure if that changes things, although it certainly has changed things with using Vino=server for remote access, which keeps crashing!  I'm thinking I should go back to an earlier version where vino-server didn't crash all the time.

---

### Post by willis11of12 on 2012-06-23
> **Spusew said:**
> The mistake can here?

I'm sorry, I'm not sure I understand what your question is.  Can you say that another way?

---

