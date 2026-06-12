---
title: "update manager not working"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by abhivyas on 2012-05-22
update manager is not working and showing following error message

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

---

### Post by cortman on 2012-05-22
> **abhivyas said:**
> update manager is not working and showing following error message

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

Quick fix- in a terminal run

```
sudo rm -r /var/lib/apt/lists/*
```

Then run

```
sudo apt-get update
```

And try running update manager again.

---

### Post by fittzwing on 2012-07-06
I'm a noob, but I recommend that you mark this thread solved.  It worked for me.  Thank you.  I'd like to know what caused the problem though, for future reference.

---

