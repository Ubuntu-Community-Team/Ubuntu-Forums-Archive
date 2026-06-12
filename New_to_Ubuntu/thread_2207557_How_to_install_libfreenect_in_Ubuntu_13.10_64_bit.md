---
title: "How to install libfreenect in Ubuntu 13.10 64 bit"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by john_smith2 on 2014-02-24
Using Ubuntu 13.10 64 bit

john@john-Aspire-5742:~$ sudo apt-get install libfreenect libfreenect-dev libfreenect-demos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libfreenect is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libfreenect' has no installation candidate

Used this tutorial [http://openkinect.org/wiki/Getting_Started](http://openkinect.org/wiki/Getting_Started)

---

### Post by monkeybrain20122 on 2014-02-24
The package is called libfreenect0.1

```
apt-cache search freenect
```

The outputs
```
freenect - library for accessing Kinect device -- metapackage
libfreenect-bin - library for accessing Kinect device -- utilities and samples
libfreenect-demos - library for accessing Kinect device -- dummy package
libfreenect-dev - library for accessing Kinect device -- development files
libfreenect-doc - library for accessing Kinect device -- documentation
libfreenect0.1 - library for accessing Kinect device
python-freenect - library for accessing Kinect device -- Python bindings

```
I suggest you install the synpatic package manager, that way it is easy to search when you are not sure about the exact name of the package. My problem with so many "sudo apt-get install blah blah" advise is that the person who gives the advise often has not looked up the up to date package names, so if they are changed the new users are left confused.
```
sudo apt-get install synaptic
```

In any case if you just install  libfreenect-dev it will pull in libfreenect0.1 as a dependency so there is no need to install that separately.

---

### Post by Vladlenin5000 on 2014-02-24
Wouldn't it be preferable to install the *freenect* (metapackage) instead? I don't know, just asking... That's what metapackages should do, I guess...

---

