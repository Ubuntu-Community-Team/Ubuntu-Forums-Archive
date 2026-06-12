---
title: "How did these files get removed from /tmp?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by bhold on 2008-04-27
Before installing 8.04 desktop over 7.10 desktop, I made a complete tar file backup of /home. After the 8.04 install was completed, I un-tarred the backup into the /tmp directory. From there, I copied files I wanted to keep into /home.

No problem so far. Tonight I was working on recovering my Firefox bookmarks. Copying the old saved bookmarks.html file over the new bookmarks.html file did not work as expected, so I decided to try a reboot. 

When the system came up from the reboot, all the un=tarred files I had placed in /tmp were gone.

I have no clue how this happened, and a review of my shell history file confirms what I already knew - I did nothing with the rm command. So where did these files go???????

---

### Post by LaRoza on 2008-04-27
I think /tmp is wiped periodically. That is why it is temporary...

---

### Post by bhold on 2008-04-27
Looks like /tmp is getting cleaned during reboot by the script 
/etc/init.d/bootclean

I would mark this thread as "Solved" but I don't see how to do it - didn't "Mark Solved" used to be under Thread Tools before the forum cleanup for 8.04?

---

### Post by pjnsmb on 2008-04-27
> **bhold said:**
> Looks like /tmp is getting cleaned during reboot by the script 
/etc/init.d/bootclean

I would mark this thread as "Solved" but I don't see how to do it - didn't "Mark Solved" used to be under Thread Tools before the forum cleanup for 8.04?

[http://ubuntuforums.org/showthread.php?t=769306&highlight=mark+solved](http://ubuntuforums.org/showthread.php?t=769306&highlight=mark+solved)


seems to be on the way..............

---

