---
title: "xubuntu software center will not install package offline"
date: 2016-06-22
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2016-06-22
Trying to install a package offline in xubuntu 16.04.
The software center just hangs and does nothing when I press install.
If there is no internet access on the system
How do I install a local package?

---

### Post by slickymaster on 2016-06-22
Can you please provide us the output of ```
apt-cache policy gnome-software
```

---

### Post by ajgreeny on 2016-06-22
You must have a network connection to use software-centre as all the packages are downloaded and installed from the Ubuntu repositories.
There are ways to do it offline but it is not simple for a new user, and of course, you will still have to download the packages somehow from the repos in order to do it this way.

If you already have the packages, as I think you may have, copy them to /var/cache/apt/archives, then use software-centre and I think it should find those packages and install them.  I do not use software-centre but have always used synaptic as an alternative, quicker and better in my opinion, and that works as I have suggested so I think SC should do as well.

---

### Post by slickymaster on 2016-06-23
> **ajgreeny said:**
> You must have a network connection to use software-centre as all the packages are downloaded and installed from the Ubuntu repositories.
There are ways to do it offline but it is not simple for a new user, and of course, you will still have to download the packages somehow from the repos in order to do it this way.

If you already have the packages, as I think you may have, copy them to /var/cache/apt/archives, then use software-centre and I think it should find those packages and install them.  I do not use software-centre but have always used synaptic as an alternative, quicker and better in my opinion, and that works as I have suggested so I think SC should do as well.

The reason I asked the OP for his gnome-software version is [bug 1573408]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573408") as he might be affected by it.

---

### Post by howefield on 2016-06-23
You could try using the terminal to install the local package.. if it is looking for dependancies or has some other difficulty you should get some sort of error message that will help you.

```
sudo apt install ~/Downloads/packagename
```

Replace "*~/Downloads/packagename*" with the actual path and file name of the package.

---

### Post by a.dusty.trail on 2016-06-23
> **slickymaster said:**
> Can you please provide us the output of ```
apt-cache policy gnome-software
```


```
:~$ apt-cache policy gnome-software
gnome-software:
  Installed: 3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2
  Candidate: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1
  Version table:
     3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 500
        500 file:/var/lib/local-apt-repository ./ Packages
 *** 3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 100
        100 /var/lib/dpkg/status
```

---

### Post by slickymaster on 2016-06-23
> **a.dusty.trail said:**
> ```
:~$ apt-cache policy gnome-software
gnome-software:
  Installed: 3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2
  Candidate: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1
  Version table:
     3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 500
        500 file:/var/lib/local-apt-repository ./ Packages
 *** 3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 100
        100 /var/lib/dpkg/status
```

Right, what I suspected. You are affect by the bug I mentioned. All you have to do is to install ```
gnome-software 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1
```At a terminal window just run```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

