---
title: "[SOLVED] chown - permission denied"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Joe Soap on 2008-06-29
I'm running hardy and have a couple of movie files that belong to root.  I want to change ownership from root to me.  I've tried it with sudo chown -R me /dir/filename but get a permission denied response.

I tried doing it as root - su'd and then ran chown -R me /dir/filename but get the same response.

The drive on which the files are stored has been formatted as a reiserfs  partition.

Any and all advice is welcome.

---

### Post by sayakb on 2008-06-29
Try:
```
sudo chmod +r /path/to/file
```

---

### Post by silkstone on 2008-06-29
I don't think you can change ownership except on ext3 partitions, but you can change access permissions. (May be wrong here - novice when it comes to this sort of thing!)

Also, I always run it as **sudo chown username:username /whatever** so it changes both owner and group, but I don't suppose that's the problem.

If you gksudo nautilus and right click on the file, select Properties and Permissions, you should be able to change these.

---

### Post by Xerp on 2008-06-29
Is the drive internal or external? Sounds like it might have been mounted read-only.

```
sudo chown username:[groupname] file
```

will always works on a read-write mounted filesystem.

---

### Post by Joe Soap on 2008-06-30
Thanks for the advice guys.

I've tried the chmod command (with sudo and as root) to no avail.

Will check whether the partition is mounted as read-only, though I'm pretty sure it's not.

Thanks for the gksudo nautilis tip.  I'll give it a shot.

Of course, I'm at work right now, so will only be able to post the results somewhat later.

---

### Post by GrumpyBob on 2008-06-30
Are you using the full path to the folder?

Robert

---

### Post by Joe Soap on 2008-07-10
@ silkstone:  I tried gksudo nautilus but when I tried to change the owner I received an error message (permission denied).

@ GrumpyBob:  I've tried it both ways, with full path (/media/sda2/) and without.  No luck :(

Any other suggestions, ideas?

---

### Post by Stunts on 2008-07-10
Hi Joe Soap.
Here's what I'd attempt:
sudo chmod 777 "files"
sudo chown username:usergroup "files"

Maybe like that it might work?

---

### Post by iaculallad on 2008-07-10
> **Joe Soap said:**
> @ silkstone:  I tried gksudo nautilus but when I tried to change the owner I received an error message (permission denied).

@ GrumpyBob:  I've tried it both ways, with full path (/media/sda2/) and without.  No luck :(

Any other suggestions, ideas?

What about using the folder location only:

```
cd /media/your_partition_location_here
sudo chown -R <username>:<group> The_Folder_Location_Here

```

---

### Post by Joe Soap on 2008-07-10
Thanks for the feedback.  Will try it (hopefully tonight) and post the results.

---

### Post by Joe Soap on 2008-07-12
Ooh-kay ...

Feeling kinda stoopid ...

The drive is formatted as fat32...

---

### Post by Stunts on 2008-07-14
LOL
There you go.
Had te be a reason for that.
Glad you found out what was wrong.
You should mark this thing as solved. =-)

---

### Post by Joe Soap on 2008-07-16
See above - ID TEN T error :)

or

The problem was discovered between the chair and the keyboard ...

---

