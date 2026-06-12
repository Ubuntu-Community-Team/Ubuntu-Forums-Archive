---
title: "flash player for ubuntu 11.10"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by ljmaximus on 2012-02-17
I just installed Ubuntu 11.10 desktop on a flash drive.  Can't figure out how to add a flash player to firefox.

Thank you.

---

### Post by wolfen69 on 2012-02-17
```
sudo apt-get install ubuntu-restricted-extras
```
Or got to the Software Center and search for flash. But the first command will give you flash and many other codecs.

---

### Post by douglas_slac on 2012-02-18
Using the above command I end up getting this message:

Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source

E: Package 'ubuntu-restricted-extras' has no installation candidate

---

### Post by winh8r on 2012-02-18
Enter in the terminal:

```
sudo apt-get update
```

then enter:

```
sudo apt-get upgrade
```


now try :

```
sudo apt-get install ubuntu-restricted-extras
```


Once this has completed you can solve most of your flash installation issues by going to this thread:


[http://ubuntuforums.org/showthread.php?t=1491268]("http://ubuntuforums.org/showthread.php?t=1491268")


Hope this is of some help to you.

---

