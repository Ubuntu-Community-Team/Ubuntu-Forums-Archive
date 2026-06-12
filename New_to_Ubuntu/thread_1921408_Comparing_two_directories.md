---
title: "Comparing two directories"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by GeordieJedi on 2012-02-06
Hi all.

I have my music collection on two hard drives (1 internal, my main master copy).
And the 2nd is on an external drive.

Now the problem is, that they are now out of sync, and I'd like to make the external drive an exact replica of the 1st internal drive.

Is there an easy way to run a comparison between the two drives?
(Possibly a GUI version)

What I'd like to achieve is -

1. To compare both directories and find the differences between them.
(If there aren't too many differences, I can manually copy across the requisite files)

2. From then onwards, I'd like to keep both dirs always synchronised.
(Something like Unison ?)


Thanks in advance for any help.

---

### Post by oldos2er on 2012-02-06
Meld, it's in the repositories. ```
sudo apt-get update && sudo apt-get install meld
```

---

### Post by ibrahimtawbe on 2012-02-07
visit this  IBM article 
[http://www.ibm.com/developerworks/aix/library/au-filesync/index.html?ca=dgr-lnxw07UNIX-File-Sync&S_TACT=105AGX59&S_CMP=grsitelnxw07](http://www.ibm.com/developerworks/aix/library/au-filesync/index.html?ca=dgr-lnxw07UNIX-File-Sync&S_TACT=105AGX59&S_CMP=grsitelnxw07)
look at 
Intelligent synchronization with rsync
search google how to use rsync

---

### Post by GeordieJedi on 2012-02-07
Thanks for the help so-far.

I appreciate it

---

### Post by GeordieJedi on 2012-03-08
Thanks very much 

I tried meld, it worked a treat. However I had far to many files to copy across manually.

So I had to use the brute force method of wiping the dir and copying the entire original dir across.

In the future I think I'm gonna try rsync or unison to keep my files in order.

---

### Post by bronquel on 2012-03-08
I have the same problem, I solved this using dirsync pro.  [http://dirsyncpro.org/](http://dirsyncpro.org/)   Its opensource, cross platform, and was the only solution I tried with a nice gui that didn't make me manually do a bunch of stuff.

---

### Post by GeordieJedi on 2012-03-08
Cool, Thanks !

That looks really useful.

Cheers.

---

### Post by dragonfriend0013 on 2012-03-08
I use rsync, running a script on startup to do the work when I boot up.  I have seen gui tools out there that use rsync, the the script i use works just fine.

---

### Post by georgelab on 2012-03-08
I do encourage rsync usage, it's an amazing tool. I'm using rsync to daily backup my file server.

---

