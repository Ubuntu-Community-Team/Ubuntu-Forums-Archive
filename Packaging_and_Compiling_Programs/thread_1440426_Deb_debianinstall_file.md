---
title: "Deb debian/install file"
date: 2010-03-27
forum: Packaging and Compiling Programs
---

### Post by ChrisB111 on 2010-03-27
I am trying to create packages to install a certain folder (and contents) to certain place on the file system. I have done most of it and the packages build without any errors but the files don't appear when the package is installed.

For instance how do I make the *foo* folder (in the source directory) and contents appear here */home/usr/foo*.

The install file looks like at the moment but it doesn't work.
```
usr/     /home/usr/foo
```

Can anyone help, and If I have got it totally wrong tell me how would I go about doing this?

Thanks,

Chris

---

### Post by SevenMachines on 2010-03-28
hi. i'll assume that you are either running dh_install in your rules file or using cdbs includes.

the entry you have above tells debhelper to install the usr/ directory in your source tree to the directory /home/use/foo/.

if your trying to install a directory foo/ from your source directory (and its contents) you would want
 
foo/ /home/usr/

seems a strange place to put it though :)

---

### Post by ChrisB111 on 2010-03-28
Thanks very much SevenMachines, you fixed my problem. I had made a mistake working out the dummy directories to post but I had omitted dh_install from my rules file. Now fixed, everything works fine.

Thanks again,

Chris

---

