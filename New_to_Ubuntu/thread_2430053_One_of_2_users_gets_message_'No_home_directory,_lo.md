---
title: "One of 2 users gets message 'No home directory, logging in with HOME=/'"
date: 2019-10-27
forum: New to Ubuntu
---

### Post by giant-paw on 2019-10-27
Hi, im counting for any help.

I've restored backup for my User **1 **and this user can't login graphically. I then created User **2 **and this user can do everything and working OK.
I want to restore my User **1 **- when I login to this user in tty1, it says```
 'No home directory, logging in with HOME=/'
```
I suppose that's the reason User **1** can't login, since User **2 **doens't get that message? How do I fix first User?

I'm using Nvidia driver nvidia-340, 
6 Gb RAM laptop, 
Intel i5 x 4 threads and 
Ubuntu Bionic Beaver 18.04.3 LTS.

Thanks

---

### Post by The Cog on 2019-10-27
Look at /etc/passwd and make sure the user's home directory is correct in there. The error is usually because the directory named in that file does not exist. It might be that the ownership or permissions on the directory don't allow the user in but my guess is that the name is wrong.

---

### Post by giant-paw on 2019-10-27
Here's output of command:
```
sudo nano /etc/passwd
root:x:0:0:root:/root:/bin/bash
...
user:x:1000:1000:G,,,:/home/user:/bin/bash
...

```Looks like it correct.

But I just found something more strange I hadn't seen before:
There's another home inside home, so **User 1 **has directory /home/home/user.
2nd user has name ubuntu, his normal path is /home/ubuntu, but also /ubuntu, which I don't know why exists. I also have folders root, usr, bin , var, etc. (no pun intended) inside /home. Looks like 'user 1' didnt see it, and it's seen from perspective of user 2, probably.
I have 1 folder owned by root:
```
sudo ls -l /home/home/user
....
drwxr-xr-x 2 user user 4096 Oct 20 14:52 Downloads
drwx------ 2 root root 4096 Oct 20 10:38
...

```

Should I delete all duplicates under /home, move /home/home/user to /home/user, delete /ubuntu, and that's it? Probably some sudo commands needed for permissions.

Thanks for help!

---

### Post by The Cog on 2019-10-27
I find your post a little confusing. A user's home cannot be two places. If /etc/passwd says it is /home/ubuntu, then that's it. /home/home/user and /ubuntu both sound wrong to me. I think the most likely explanation is having accidentally restored the backup to the wrong place, but only looking at the contents will tell you if that's the case. Having folders like root, usr, bin etc inside home strongly support the idea of having restored a backup of the entire system to /home rather than just restoring user1's home folder to /home.

I would be inclined to delete the rot, bin, var etc. folders from /home as they are just copies of the real ones under /. Then, (if /home/user1 does not exist) just move /home/home/user1 to /home/user1. But have a look to ensure you are not deleting things you might regrtet first.

---

### Post by giant-paw on 2019-10-28
It is indeed, I'm myself confused - Just when I was deleting this strange folder /ubuntu, /home/ubuntu gone as well. It looks like copies of bin, var, dev, are linked to their originals, which is very weird to me. 
It's such an Epic Fail for sure.

So, Thanks The Cog, despite all of that, I did not learn nothing from this thread. Next time - smarter restoring backup.

---

