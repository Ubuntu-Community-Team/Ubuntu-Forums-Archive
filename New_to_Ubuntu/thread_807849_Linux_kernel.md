---
title: "Linux kernel"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by x88a on 2008-05-26
i am using Ubuntu 8.04.
i need to know if "linux-kernel-headers" and "linux-kernel-sources" have been installed in my comp.
How do i check?
TQ

---

### Post by hyper_ch on 2008-05-26
check in synaptic

---

### Post by sisco311 on 2008-05-26
or from the terminal:
```
aptitude search linux-kernel-headers
```and
```
aptitude search linux-source
```> Each search result is listed on a separate line. The first
           character of each line indicates the current state of the package:
           the most common states are p, meaning that no trace of the package
           exists on the system, c, meaning that the package was deleted but
           its configuration files remain on the system, [B]i, meaning that the
           package is installed[/B], and v, meaning that the package is virtual.
           The second character indicates the stored action (if any; otherwise
           a blank space is displayed) to be performed on the package, with
           the most common actions being i, meaning that the package will be
           installed, d, meaning that the package will be deleted, and p,
           meaning that the package and its configuration files will be
           removed. If the third character is A, the package was automatically
           installed.

---

### Post by x88a on 2008-05-26
i get:-
v   linux-kernel-headers

so does this mean it is installed?
what does virtual mean?


i also get:-
p   linux-source                    - Linux kernel source with Ubuntu patches   
v   linux-source-2.6                -                                           
p   linux-source-2.6.22             - Linux kernel source for version 2.6.22 wit

what does 3 diff source mean?

i am soooo lost
pls help

TQTQTQ

---

### Post by kpkeerthi on 2008-05-26
```
aptitude show <package-name>
``` prints information about <package-name> including installed status. 

Checking in synaptics is probably the easiest way for you. Search for a package. If it is marked in green, it is installed.

---

### Post by sisco311 on 2008-05-26
No, is not installed. If you want to install the packages type:
```
sudo aptitude install   linux-kernel-headers linux-source
```

As mentioned by hyper_ch you can use Synaptic Package Manager to search and install packages.
System -> Administration -> Synaptic Package Manager

---

### Post by x88a on 2008-05-26
i get 0 search results for linux-kernel-headers in Synaptic

2 search results for linux-source
They are: linux-source and linux-source-2.6.22
What is the difference?
Which one should i install?
i am using Ubuntu 8.04

TQ

---

### Post by sisco311 on 2008-05-26
I think you need to install *linux-header-generic* and *linux-source*.

From synaptic:

linux-source:> 
This package will always depend on the latest Linux kernel source code
available. The Ubuntu patches have been applied.
linux-header-generic:
> This package will always depend on the latest generic kernel headers
available.

---

### Post by x88a on 2008-05-26
i get 0 search results for linux-header-generic :(

---

### Post by sisco311 on 2008-05-26
> **x88a said:**
> i get 0 search results for linux-header-generic :(
sorry, it's linux-header**s**-generic

---

### Post by kpkeerthi on 2008-05-26
You need to install **linux-headers-generic** and **linux-source**.

```

sudo aptitude install linux-headers-generic linux-source

```

[http://packages.ubuntu.com/hardy/linux-headers-generic](http://packages.ubuntu.com/hardy/linux-headers-generic)
[http://packages.ubuntu.com/hardy/linux-source](http://packages.ubuntu.com/hardy/linux-source)

---

### Post by kpkeerthi on 2008-05-26
The kernel-header package contains the C header files for the linux kernel. You may need this package to build a program from source.

The linux-source package contains the kernel source code.

---

