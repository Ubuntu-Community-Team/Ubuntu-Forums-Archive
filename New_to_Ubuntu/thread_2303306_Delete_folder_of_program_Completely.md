---
title: "Delete folder of program Completely"
date: 2015-11-17
forum: New to Ubuntu
---

### Post by prog-researcher on 2015-11-17
i'm new to Ubuntu Really need help in this problem 
Now i installed old version of a program that used a port for its processes , i deleted the folder of the program by `right click .. remove` and didn't know that it has any files in other place !! and didn't know that may be a process using port 

i installed new version of the program and every time i ran the program , old version folder created and `empty` !! 

Now i want to delete old version folder completely in right way 
i searched for `PID` of the old version but it gave nothing !! sure because i deleted the folder of the program , HOW can i solve this

---

### Post by grahammechanical on 2015-11-17
Did you remove the program? Perhaps the old version is still installed and it is that which is loading. How did you install the old version of this program? Through Ubuntu Software Centre? How did you remove it?

Regards.

---

### Post by prog-researcher on 2015-11-17
i installed it by commands in terminal not through software center , and i removed it by deleted the folder only , i knew after that , it's wrong way to uninstall program like that !

---

### Post by cariboo on 2015-11-18
You can't uninstall a program by just deleting a folder, as there are files spread all over the / directory. The Debian/Ubuntu way is to use apt get, eg:

```
sudo apt-get purge <package name>
```

You can also use Synaptic Package Manager to completely remove a package.

---

### Post by prog-researcher on 2015-11-18
i knew that after deleted the folder but there is no files i guess still in the directory except the empty folder of old that created every time i ran new version ?

i  used the above command but got unable to locate package , and couldn't find any package by regex

---

### Post by steeldriver on 2015-11-18
You will need to tell us how you installed it specifically - what actual terminal commands did you use?

---

### Post by howefield on 2015-11-18
Might help to know the program you are trying to uninstall, is it related to your other thread [http://ubuntuforums.org/showthread.php?t=2303034](http://ubuntuforums.org/showthread.php?t=2303034) ?

---

### Post by Topsiho on 2015-11-18
This is a question that might contain the answer how to solve the problem. Just don't execute it before other forum readers have commented on it:
Is it not an idea just to install the program again (using Synaptic, or apt-get in the terminal), and THEN to remove it the correct way?

Topsiho

---

### Post by prog-researcher on 2015-11-18
here the link of how to install storm 
[http://10jumps.com/blog/storm-installation-single-machine ]("http://10jumps.com/blog/storm-installation-single-machine")

i used apt-get remove but gave me that 
got unable to locate package , and couldn't find any package by regex

---

### Post by prog-researcher on 2015-11-21
any help ?

---

### Post by sandyd on 2015-11-22
Hi,
what is the exact name of the package and path of the folder you removed?

Or was it ZeroMQ/JZMQ that you removed?

If it was ZeroMQ/JZMQ, do this.

In the folder that you ran "./configure" for the **current** version, run 
```

sudo make uninstall
```

Don't know if the ZeroMQ/JZMQ source code supports this, but most should

Then, get the exact **old version** that you used and run 
```
./configure
``` in the folder that holds it.
If you added any options to ./configure when running it in the old version, add them as well.

Compile it again, install it again, uninstall cleanly.
```

make
make install
sudo make install
sudo make uninstall

```

If you want to want to remove it, and there is no support for make uninstall, just place the installed files somewhere else, and you can remove the folders manually. It might be faster to do this instead of doing make install again - it's your choice.

You can do that by adding "--prefix=/path/" to the ./configure options
For example:
```

./configure --prefix=/tmp/tmpinstall

```

All the folders/files that would be created when you ran make install are now in /tmp/tmpinstall, and you can manually remove them by checking the paths in /tmp/tmpinstall. If I remember correctly, by default, ./configure installs in /usr/local, so you can start there.

In the future, you can use [CheckInstall]("https://help.ubuntu.com/community/CheckInstall") instead to make it easier to remove.

---

