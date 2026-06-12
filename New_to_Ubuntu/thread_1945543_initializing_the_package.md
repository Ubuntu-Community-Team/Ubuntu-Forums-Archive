---
title: "initializing the package"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by jiangchongyi on 2012-03-23
Hello,
 
Everytime I turn up the ubuntu the following infomation comes up:
 
Could not initialize the package information
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
 
What should I deal with it ?
 
Any help will grateful!

---

### Post by Frogs Hair on 2012-03-23
Run the following in the terminal and post the output in code tags using the # symbol on the reply tool bar. again```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by jiangchongyi on 2012-03-23
> **Frogs Hair said:**
> Run the following in the terminal and post the output in code tags using the # symbol on the reply tool bar. again```
sudo apt-get update
``````
sudo apt-get upgrade
```
 
 
I try as you suggested but it still can not work.
 
The following note came up:
 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
 
what should I do?

---

### Post by jerrrys on 2012-03-24
try this

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by jiangchongyi on 2012-03-29
> **jerrrys said:**
> try this
 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
 
 
 
 
Problem solved&#65281;
Thanks a lot~

---

### Post by raja.genupula on 2012-03-29
glad to hear , now mark the thread as solved from thread tools .

---

