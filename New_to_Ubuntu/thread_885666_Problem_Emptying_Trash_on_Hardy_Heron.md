---
title: "Problem Emptying Trash on Hardy Heron"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Billsey on 2008-08-10
I just ran into a problem that I have never seen before on Ubuntu: I have tried to delete files (just an archive and directories of spare fonts, nothing critical) and only later discovered that the permissions somehow got set to "root" instead of to me. Now I can't get those files out of the trash because, well, I can't find the trash in the actual filesystem. The files will not either delete or move out of the trash without the permissions getting changed to what they should be, and I can't find them in the filesystem to change their permissions. Help!

---

### Post by rampageoberon on 2008-08-10
I think this command will empty the trash.

```
sudo rm .local/share/Trash/files/*
```

---

### Post by sisco311 on 2008-08-10
Trash is located in ~/.local/share/Trash

---

### Post by bpowell2005 on 2008-08-10
> **Billsey said:**
> I just ran into a problem that I have never seen before on Ubuntu: I have tried to delete files (just an archive and directories of spare fonts, nothing critical) and only later discovered that the permissions somehow got set to "root" instead of to me. Now I can't get those files out of the trash because, well, I can't find the trash in the actual filesystem. The files will not either delete or move out of the trash without the permissions getting changed to what they should be, and I can't find them in the filesystem to change their permissions. Help!

Hmm, this is strange!

Trash is located in your home directoroy at: ~/.local/share/Trash

You could go in there, go into the Files directory, "sudo chown username:username *.*" (replace Username with your username) this would give you ownership of the files and then you should be able to delete them...you may want to also delete the files in the Info directory as well.

---

### Post by Ryadt on 2008-08-10
Try ```
gksudo nautilus
``` and worked it out from there.

---

### Post by Billsey on 2008-08-10
Thank you, Folks.

Finding the location of the files allowed me to remove them. I used "sudo rm -r *" on the contents of the "files" directory (since it involved directory trees) and "sudo rm *.*" on the contents of the "info" directory. Again, many thanks.

Any chance of getting this valuable information put into a troubleshooting section of the installed help?

---

### Post by xfred on 2008-09-12
I have a similar problem - files in the Trash that won't delete.  However both folders ~/.local/share/Trash/files and ~/.local/share/Trash/info show up as empty:

```
xxxx@yyyy:~/.local/share/Trash/files$ ls -al
total 8
drwxrwxrwx 2 xxxx xxxx 4096 2008-09-12 13:51 .
drwx------ 4 xxxx xxxx 4096 2008-09-01 12:41 ..
xxxx@yyyy:~/.local/share/Trash/files$ 
```

and:
```
xxxx@yyyy:~/.local/share/Trash/info$ ls -al
total 8
drwxrwxrwx 2 xxxx xxxx 4096 2008-09-12 13:55 .
drwx------ 4 xxxx xxxx 4096 2008-09-01 12:41 ..
xxxx@yyyy:~/.local/share/Trash/info$ 
```

I followed the instructions anyhow but when I open the Trash on the desktop I still get the offending files showing up.

I suspect the problem is that the files were not located on the same physical disk when I deleted them (the 5th internal drive in fact), but I don't know where to look for these.  Any suggestions?

---

### Post by SunnyRabbiera on 2008-09-12
This is a bug I encountered too, but for me it went away after a few updates.

---

### Post by xfred on 2008-09-12
That's odd; I just checked and my system has all updates installed.  But thanks.

---

### Post by xfred on 2008-09-12
Problem sorted.  Seems there are .Trash directories on each separate physical hard-drive.  In fact for some reason the hard-drive in question had two of them in its root directory, so I just had to own and nuke the contents of both (and fix permissions on the one for which they were messed up).  Probably just leftovers from a previous installation I'm guessing.

---

### Post by Billsey on 2008-09-14
I was going to ask if you had a separate drive connected via USB. Whenever I do that, a .Trash-1000 folder shows up in that drive's root.

---

### Post by simtaalo on 2008-09-14
i have had a folder thats been in the trash for ages that doesnt seem to delete. 

i tried the command given above

sudo rm .local/share/Trash/files/*

but i get the error

> rm: cannot remove `.local/share/Trash/files/untitled folder': Is a directory


how do i get past this?

---

### Post by drs305 on 2008-09-14
I've written a tutorial on finding and deleting trash throughout your system. You can find it in the tutorial forum here:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

