---
title: "Archive manager 3.6.0 - cannot add files anymore"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by xtrailrunner on 2012-10-21
Hi all,
I have upgraded recently to Ubuntu 12.10 with Cinnamon 1.6.3.
When I want to use Archive Manager (file-roller 3.6.0) with Nautilus 3.4.2 I cannot add files to an existing zip archive.
(1)  When I try to add a file using Archive Manager's menu:  Add File nothing happens
(2)  When I drag&drop a pdf file to an existing zip archive I get "You can't add an archive to itself"
(3) When I compress several files into a zip file it works.
(4) When I try to create a new archive using Archive Manager's menu: New and add files afterwards I get error "An error occured while loading the archive".
I have no clue how to solve this problem.

With Nemo 1.0.5 I have the same problem.

---

### Post by samcompton on 2012-10-23
I'm getting the exact same thing.

---

### Post by pqwoerituytrueiwoq on 2012-10-23
[http://packages.ubuntu.com/precise/file-roller#pdownload](http://packages.ubuntu.com/precise/file-roller#pdownload)
down grade file roller and all will be good
to prevent it from upgrading run this
```
echo "file-roller hold" | sudo dpkg --set-selections
```
you may need to lock it in [synaptic](apt:synaptic) also

i am xubuntu with thunar

---

### Post by xtrailrunner on 2012-10-24
Hi, thanks.
What is the bug number for that issue ?

---

### Post by pqwoerituytrueiwoq on 2012-10-24
there are several bugs in it, i don't know the numbers sorry

---

### Post by Thunder7102 on 2013-05-31
Can someone give me a walkthrough of how to install this? If I try to manually dpkg, I get a dependency error. Is there a way to get those installed and a version which works for 13.04? I know this is a grave-dig, but it's the only relevant topic to the problem I'm having.

---

### Post by Renaissance Hacker on 2013-06-12
**Hi Thundar7102**

1) Remove file-roller through term or archive manager in Ubuntu Software Center

2) Install 3 Files

    [http://packages.ubuntu.com/precise/liblaunchpad-integration-common](http://packages.ubuntu.com/precise/liblaunchpad-integration-common) liblaunchpad-integration-common
    [http://packages.ubuntu.com/precise/liblaunchpad-integration-3.0-1](http://packages.ubuntu.com/precise/liblaunchpad-integration-3.0-1) liblaunchpad-integration-3.0-1
    [http://packages.ubuntu.com/precise/file-roller#pdownload](http://packages.ubuntu.com/precise/file-roller#pdownload) file-roller (3.4.1-0ubuntu1)

3) Locks file in term ```
echo "file-roller hold" | sudo dpkg --set-selections
```

4) Lock file-roller in synaptic package manager via package

**Hope this helps I had the same issue in 13.04 Ubuntu and it resolved after this downgrade**

---

