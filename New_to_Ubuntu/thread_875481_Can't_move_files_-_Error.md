---
title: "Can't move files - Error"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by gustasonfrever on 2008-07-30
For some reason I can't move files into or out of the "My Music" folder I have inside of the "Music" folder. I dragged the "My Music" folder off of an external hard drive. The file was originally on an XP system. If its relevant, there is a lock in the top right corner of the file when I view it. When I tried to move a torrent into the "My Music" folder I got an error message that said

Error while moving "Ubuntu Torrents".
There was an error moving the file into /home/justin/Music/My Music.
Error moving file: Permission denied

I have no idea whats wrong so any advice is appreciated

---

### Post by frank002 on 2008-07-30
Right click the file you want to move  click Properties and check the permissions. If the owner is "root" you can change the ownership to yourself using sudo chown.

---

### Post by ConMan318 on 2008-07-30
```

sudo chown **yourUserName path/to/folder**

```

will transfer ownership from root user to you.

---

### Post by markjensen on 2008-07-30
what is the output of the command
**ls -al ~/Music/**

I am looking for the possibility that you have files or folders that are owned by "root" instead of "justin"

If you find this is the case, you can do a
**sudo chown -R justin ~/Music** to change everything in there to be owned by you.

---

### Post by gustasonfrever on 2008-07-30
When I type that in I get 
justin@justin-laptop:~$ ls -al ~/Music/
total 16
drwxr-xr-x  4 justin justin 4096 2008-07-30 18:59 .
drwxr-xr-x 39 justin justin 4096 2008-07-30 19:13 ..
dr-x------  8 justin justin 4096 2008-07-21 21:19 My Music
drwxr-xr-x  4 justin justin 4096 2008-07-30 18:59 Ubuntu Torrents
justin@justin-laptop:~$

And then when I do sudo chown

justin@justin-laptop:~$ sudo chown justin home/justin/music/my music
[sudo] password for justin: 
chown: cannot access `home/justin/music/my': No such file or directory
chown: cannot access `music': No such file or directory
justin@justin-laptop:~$

I re-read your post and then typed in what you told me 
justin@justin-laptop:~$ sudo chown -R justin ~/Music
justin@justin-laptop:~$ 

But I still can't move anything into/out of the folder

---

### Post by ConMan318 on 2008-07-30
```

chmod 755 ~/Music/My\ Music

```

You don't have 'write' rights to that directory.  The above will give you those rights.

---

### Post by gustasonfrever on 2008-07-30
That was it! Thanks a lot

---

