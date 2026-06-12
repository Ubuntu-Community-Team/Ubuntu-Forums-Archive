---
title: "How can i install KDevelop in Ubuntu"
date: 2007-03-30
forum: Programming Talk
---

### Post by Gefox4 on 2007-03-30
Ubuntu now is not available for KDevelop C/C++. So how can i install that package? Is there any package like that, plz tell me the name of it! :confused: :confused:

---

### Post by lnostdal on 2007-03-30
When you find some software you want to install, do not download it from the Internet. Do not even download it from the homepage of the software itself!

Use the Ubuntu package manager to install software.

```

sudo aptitude install kdevelop

```

Please see: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html) and make sure you understand as much of that as possible.

---

### Post by Gefox4 on 2007-03-31
But Ubuntu now is not available for Kdevelop, so I can't find that package to add it. Is there any package like that? And what's it's name?

---

### Post by lnostdal on 2007-03-31
i do not understand what you are saying .. if aptitude is unable to find a package named `kdevelop' you need to enable the universe-repositories: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html) because that is where `kdevelop' is 

root@ibmr52:~# aptitude show kdevelop
Package: kdevelop
State: installed
Automatically installed: no
Version: 4:3.4.0-0ubuntu3
Priority: optional
Section: **universe/kde**

---

### Post by Gefox4 on 2007-03-31
> **lnostdal said:**
> i do not understand what you are saying .. if aptitude is unable to find a package named `kdevelop' you need to enable the universe-repositories: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html) because that is where `kdevelop' is 

root@ibmr52:~# aptitude show kdevelop
Package: kdevelop
State: installed
Automatically installed: no
Version: 4:3.4.0-0ubuntu3
Priority: optional
Section: **universe/kde**

Because my English is not well. I'm using Ubuntu 6.06 LTS. When I go to Add/Remove, I search KDevelop package, it result that "Could not found" that package. I search it in the update package but not see it.

---

### Post by lnostdal on 2007-03-31
alright .. try to use synaptic or aptitude when searching for it

synaptic is found in the menus: System -> Administration -> Synaptic Package Manager

aptitude is used from the terminal, for instance: sudo aptitude search kdevelop

..if it isn't in the repositories (you cannot find it), you need to enable universe as described in the link i gave you.

---

### Post by Gefox4 on 2007-03-31
> **lnostdal said:**
> alright .. try to use synaptic or aptitude when searching for it

synaptic is found in the menus: System -> Administration -> Synaptic Package Manager

aptitude is used from the terminal, for instance: sudo aptitude search kdevelop

..if it isn't in the repositories (you cannot find it), you need to enable universe as described in the link i gave you.

Thanks u. I've done. It's working.

---

