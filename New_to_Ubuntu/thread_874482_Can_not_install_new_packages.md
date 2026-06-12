---
title: "Can not install new packages"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by jamil_1 on 2008-07-30
I am unable to either install or upgrade packages. When ever I try to do so I get an error:



[I]Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing libnbio0 (NewVersion1)
E: Problem with MergeList var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
[/I]

---

### Post by iaculallad on 2008-07-30
Try this in your terminal if it resolve that problem:

```
sudo apt-get update -o APT::Cache-Limit=25165824
```

---

### Post by jamil_1 on 2008-07-30
Thanx man for the help. Will u please tell me why was I gettig that error ?

---

### Post by tinny on 2008-07-30
To get more details about what is going on,

Open a terminal...
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

The above commands will clean and update the ubuntu package management system (APT). Then all packages that require updating will be updated.

If this works then your system is in good shape. If it fails please post back the results.

What packages are you trying to install? You may have to enable the universe or multiuniverse repositories. How are you trying to install the package? APT, Synaptic?

---

### Post by iaculallad on 2008-07-30
> **jamil_1 said:**
> Thanx man for the help. Will u please tell me why was I gettig that error ?

For a more detailed explanation regarding this, try reading this launchpad bug information from [launchpad.net]("https://bugs.launchpad.net/debian/+source/apt/+bug/24626").

---

### Post by tinny on 2008-07-30
> **iaculallad said:**
> For a more detailed explanation regarding this, try reading this launchpad bug information from [launchpad.net]("https://bugs.launchpad.net/debian/+source/apt/+bug/24626").

Opps I completely misunderstood this thread :)

---

