---
title: "Wubi partitions and install"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by braufrau on 2011-10-08
HI,

  sorry to ask such a pathetic question but ...

I have installed ubuntu on a netbook with a 250GB HD.
About 30GB of the C: drive was taken up with windows and bunch of documents that are still there.
About 10GB of D:\ drive was taken up with some more documents, that are still there but I've made a link from my ubuntu documents directory to that directory.

I have somehow mounted the c:\ drive under ubuntu and its called 107GB Filesystem.

I did a wubi install on D:\ and I think I chose 30GB of installation space.

So now my questions.
Is the 30GB I chose for the wubi install the limit of how much I can store under the linux filesystem?
Or will my photos and videos etc. keep expanding into the complete D:\ partition?
I guess I'm asking if I will run out of space any second now if I keep storing files under /home/sam/Photos ~/Documents ~/Videos etc. etc. ??

---

### Post by bcbc on 2011-10-08
The wubi virtual disk is a fixed size - in your case 30gb - and it won't expand automatically. It's also not the best idea to move important data on to the virtual disk, as it's saved as a single file on the /host (in your case D:) and any corruption on the virtual disk can lead to full loss of data.

My advice is to leave personal files on the /host ntfs file systems and reference them from Wubi or do a direct install.

---

### Post by braufrau on 2011-10-09
Thanks bcbc.

So I think the time has come to change this windows computer with a bit of linux, to a linux one with a bit of windows.

I think the simplest thing might be to back up my data and make a windows recovery CD and reinstall.
Do you think so?

---

### Post by anewguy on 2011-10-09
Hard to say, but I would at least recommend you do a true ubuntu installation - perhaps dual boot with your existing Windows installation - not wubi.  wubi is really only meant as a test bed - "try me - if you like me do a 'real' install".  Whether you keep your existing Windows and dual boot with ubuntu, run ubuntu only with Windows in a virtual machine within ubuntu, etc., is really dependent on what you want to do - especially taking into consideration what you do with your existing Windows installation.  Are you a gamer?  Do you use any specialized software?  While there are Linux equivalents for most software, it doesn't mean that what you are used to is actually what you would be running.  Same with games.  What's your CPU and memory information like?  Will it support a virtual machine?

These are a few of the questions you really need to research on your own - we can guide you if you ask a specific question.  Google/Yahoo!/Bing/etc. are good friends for you in this case - if you use a program called "blinky", the search string:

ubuntu 11.04 blinky

would usually return many references to check.  Be sure to ask back here as well, but keep in mind we need to know task by task instead of just in general.

This rather invalidates your wubi question - so perhaps you might want to post your total disk capacity, what the current partitions are and how they are used (remember you need to keep any form of recovery/drivers partition(s) as well).  This will provide us with more information to try to help you.

Dave ;)

---

### Post by bcbc on 2011-10-10
> **braufrau said:**
> Thanks bcbc.

So I think the time has come to change this windows computer with a bit of linux, to a linux one with a bit of windows.

I think the simplest thing might be to back up my data and make a windows recovery CD and reinstall.
Do you think so?

If you're talking about reinstalling Windows, then you need more than a recovery CD - that's just to repair an existing install. It's a good idea to create system restore DVD's if you don't have the original windows DVD (even if you aren't going to reinstall windows it's good to have a backup plan).

My first choice would be to shrink the Windows partition - reinstalling can be a pain. 

In terms of moving from Wubi to a partition install, you can either backup and reinstall direct. Or you can create the partitions manually and [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi install. Migrating preserves the program/settings/data on the wubi install - so it's useful if you've done a lot of customization.

---

