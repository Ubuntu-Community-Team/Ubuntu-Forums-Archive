---
title: "Libraries not found"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by pquinnet on 2008-07-08
I am familiar with UNIX but not as much with Linux.  I am trying to install Pingus software and have installed all the needed libraries and verified their existence and location. I added /usr/lib and /var/lib to my PATH and verified that via "env".  However, when I run scons, it says all the libraries I installed via ACCENT(??), are "libray libboost_signals not found" same for png etc.  Is there another ENV parm I need to  point to where the libraries are at ??  In UNIX AIX, there is a
LIB parm for the ENV that points to where libraries are at.

thanks,  pquin

---

### Post by Cypher on 2008-07-08
Please run the following command on the executabe
```

ldd scons

```
This will show all the libraries needed by the executable and where, if at all, they were found.

Next if you've installed the needed libraries into the standard librari directories then you shouldn't have do anything other than running 'ldconfig' to regenerate the cache file used to find the libraries.

If you've installed the libraries into a non-standard directory, then you will want to add that directory to file in the /etc/ld.so.conf.d directory and then run 'ldconfig' again.

As long as you run the "ldd scons" command don't see any "Not found" messages, you can have confidence that the program will run..

---

### Post by ChameleonDave on 2008-07-08
Are you talking about *Pingus*, the clone of the game *Lemmings*?

It is in the repositories (see [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)).

Just do the following command:

```

sudo apt-get install pingus

```

---

### Post by pquinnet on 2008-07-08
> **Cypher said:**
> Please run the following command on the executabe
```

ldd scons

```
This will show all the libraries needed by the executable and where, if at all, they were found.

Next if you've installed the needed libraries into the standard librari directories then you shouldn't have do anything other than running 'ldconfig' to regenerate the cache file used to find the libraries.

If you've installed the libraries into a non-standard directory, then you will want to add that directory to file in the /etc/ld.so.conf.d directory and then run 'ldconfig' again.

As long as you run the "ldd scons" command don't see any "Not found" messages, you can have confidence that the program will run..
thanks !!   The library's not found were coming when I ran scons within the Pingus directory that had all the gunziped files and directories.  It said I was missing all the libraries that Pingus needed. But I had read the doc and installed all the libraries and verified there existence and location. SCONS seem to run just fine.  Unless you run scons from a sub-directory within the Pingus master directory where I ran scons from.  I will experiment with what you have provided.  Thanks for the help.    pq

---

### Post by pquinnet on 2008-07-08
> **ChameleonDave said:**
> Are you talking about *Pingus*, the clone of the game *Lemmings*?

It is in the repositories (see [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)).

Just do the following command:

```

sudo apt-get install pingus

```
Yes, I am.  I found it on a list of free game software and was just trying to see what Linux can produce for games.  I downloaded a whole bunch of demo's of $$$games to see what they look like before I buy any.  I can do the apt-get and that is straight forward. I was looking to setup my environment for future configures/makes/installs.   I will load the game tonight for some fun and enjoyment then go back and research why my libraries are not being found by scons or make.    thanks ...pq

---

