---
title: "Where do Compiled applications go?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by FlintyVamp on 2008-08-06
Hey,

Sorry if compiled isn't the correct term to use. This question is completely out of curiosity. I downloaded Banshee from source and compiled and all went well. 

I was wondering where the application files go. Do they go into the guts of Ubuntu with the many other applications or do they stay in the folder i compiled the application in? Am I safe to delete the folder with the source in now? 

Cheers,
FlintyVamp

---

### Post by cgkades on 2008-08-06
They could go to /bin /usr/bin /usr/sbin /usr/local/bin or /usr/local/sbin depending.

---

### Post by Pogeymanz on 2008-08-06
EDIT: Agreeing with what jabobmp92 said below; if you only issued the command "make" to compile it, then it will only be in the source directory. If you then issued "make install," it will be in a directory deeper in your system- likely /usr/local/bin.

If you only did a "make," then I think the following instructions might help make it launchable like the other applications on your system.

There are a few more steps to do before it becomes like your other applications.

I'm not sure on the "proper" way of doing this. I believe you can just copy the binary that was created from compiling into a directory like /usr/bin and then do a "chmod 777 [path to binary]" to make it executable for all users. Then if you open a terminal and type the name of the program, it should launch.

---

### Post by jpeddicord on 2008-08-06
A lot of "from-source" distributions store binaries, libraries, and files in /usr/local (making /usr/local/bin, /usr/local/share, etc). Some source dists (and .debs) store with a root of /usr, meaning that binaries are in /usr/bin, libraries are in /usr/lib, and shared files in /usr/share. Some applications may be different from that even.

> I'm pretty sure if you just did a standard "make, make intall" routine, then the application is in the source folder. To launch it, you must use the entire location`make install` installs the application to the system, usually in /usr/local as I said above. If you just do `make`, then it is kept in the source folder.

---

### Post by Nepherte on 2008-08-06
You can specify that when you run ./compile with the --prefix option. For example:
```
./configure --prefix=/usr
```

---

### Post by Pogeymanz on 2008-08-06
> **jacobmp92 said:**
> A lot of "from-source" distributions store binaries, libraries, and files in /usr/local (making /usr/local/bin, /usr/local/share, etc). Some source dists (and .debs) store with a root of /usr, meaning that binaries are in /usr/bin, libraries are in /usr/lib, and shared files in /usr/share. Some applications may be different from that even.

`make install` installs the application to the system, usually in /usr/local as I said above. If you just do `make`, then it is kept in the source folder.

Oh, I see. Thanks for clearing that up. Since I've been using Archlinux, I have forgotten stuff like that.

I'll edit my post to avoid future confusion.

---

