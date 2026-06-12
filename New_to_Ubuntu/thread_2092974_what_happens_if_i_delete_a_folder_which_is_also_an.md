---
title: "what happens if i delete a folder which is also an active mount point"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Yougo on 2012-12-09
I have googled, but the internet seems to like beating around the bush with this, so here´s the question:

What happens when i (sudo) delete a folder to which a drive is mounted?:-k
-will it be refused?
-will it delete the folder, causing the mount point to be in limbo?
-will it proceed to delete every file in the drive?
-will it cause a black hole, growing untill it sucks in the world at the 21st? :popcorn:

I know, one way to find out is to do it, but all the currently mountable drives i have, contain files i'm not willing to gamble with.

If your Google-fu is stronger than mine, or if you tried and lived, teach this grasshopper.

-------

answer:

**it's a bad idea!**

it will delete all files inside the mounted drive, but can't remove the folder itself because the 'device is busy'
you end up removing what you want to keep, and keeping what you wanted to remove. 

if you want more on the subject, read below.

---

### Post by Cheesemill on 2012-12-09
Interesting question.

I would presume that it would delete the mount point ***and*** all of the files it contains (for example 'sudo rm -rf /' will delete everything on your drive, even though / is just a mount point for the root filesystem), however, I haven't tried this either so will be waiting with interest for any replies.

[SIZE=1]**[COLOR=Red]PLEASE DON'T RUN THE ABOVE COMMAND, IT WILL DESTROY YOUR SYSTEM !!![/COLOR]**[/SIZE]

---

### Post by mcduck on 2012-12-09
It would delete the mount point and all contents of the drive mounted there (or at least all the files you have the required permissions to remove).

---

### Post by Cheesemill on 2012-12-09
Just had a quick play around as I didn't know the answer (and had some unallocated space lying around).

It looks like it will delete the contents of the mount point successfully but then give an 'cannot remove <DIR>: Device or resource busy' error when trying to remove the actual mount point itself. This seems to make sense, you wouldn't want the rm command to be able to delete mount points, you should handle that sort of thing properly with the mount command.

For situations where you are deleting a directory which contains a mount point inside it there is a related option available --one-file-system (from 'man rm').
>        --one-file-system
              when removing a hierarchy recursively, skip any directory that is on a file system different from that of the corresponding command line argument
You can see the output of my test session below:

```
rob@arch:~$ mount | grep '/dev/sdb2'
/dev/sdb2 on /home/rob/test type ext4 (rw,relatime,data=ordered)
rob@arch:~$ 
rob@arch:~$ ls
total 4.0K
drwxr-xr-x 2 rob users 4.0K Dec  9 18:51 test
rob@arch:~$ 
rob@arch:~$ touch test/testfile{1,2,3,4,5}
rob@arch:~$ 
rob@arch:~$ ls test/
total 0
-rw-r--r-- 1 rob users 0 Dec  9 19:04 testfile1
-rw-r--r-- 1 rob users 0 Dec  9 19:04 testfile2
-rw-r--r-- 1 rob users 0 Dec  9 19:04 testfile3
-rw-r--r-- 1 rob users 0 Dec  9 19:04 testfile4
-rw-r--r-- 1 rob users 0 Dec  9 19:04 testfile5
rob@arch:~$ 
rob@arch:~$ sudo rm -rf test 
rm: cannot remove 'test': Device or resource busy
rob@arch:~$ 
rob@arch:~$ ls test/
total 0
rob@arch:~$ 
```

---

### Post by BrokenLines on 2012-12-09
> **Yougo said:**
> 
-will it delete the folder, causing the mount point to be in limbo?
-will it cause a black hole, growing untill it sucks in the world at the 21st? :popcorn:
  
I got a kick out of that..
Ah, yeah you see... If you delete a mount point through an application, let's say GParted for example that contains Windows 7 Ultimate with over 45GBs of videos/music and P90X you will lose everything. BUT if you are currently mounted to it then it wont allow it. Or for me it didn't.

---

### Post by Yougo on 2012-12-10
thank's all,

thats what i guessed would happen. i was actually messing around with a script for mounting/unmounting my network drive through the unity launcher, and thankfully read it through before i ran it.

it was set to remove the /media/[drive] folder regardless of mountpoint, and would have wiped my 500GB network drive :p

@BrokenLines, i think you are talking about partitions. that's a different thing. you can mount a partition to a location in the folder tree. that folder is then called a mount point. removing a partition indeed removes all data in it, and can't be done if that partition is currently mounted (though unmounting is easily done if you're goofing about...)

i'll set this thread to [solved] and put the solution in the first post to ease the lives of people with weak google-fu.

---

