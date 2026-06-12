---
title: "Can not update"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by Dawnbandit on 2012-08-05
I tried the sudo apt-get configure -a and got this error "dpkg: error: reading package info file '/var/lib/dpkg/status': Is a directory"

---

### Post by Miljet on 2012-08-05
> E: Problem opening /var/lib/apt/lists/Ubuntu%2010.04%20LTS%20%5fLucid%20Lynx%5f%20-%20Release%20i386%20(20100429)_dists_lucid_restric ted_binary-i386_Packages

There is an unexpected, and unexplained, space in the word "restricted." Not sure how or why it got there, but I would suspect that it might be part of your problem.

---

### Post by NikTh on 2012-08-05
Hi , 
you can use below commands to clean up a little 

```
sudo apt-get clean all 
sudo apt-get autoremove
sudo apt-get autoclean 
sudo rm  /var/lib/apt/lists/* -vf
sudo apt-get update
```The fourth command will remove the damaged list and when you run the fifth command it will replace it with a new list.

If error occur in last command then run below command
```
sudo mkdir /var/lib/apt/lists/partial/
``` and then again 
```
sudo apt-get update
```Thanks

---

### Post by wildmanne39 on 2012-08-05
*Thread moved to **Absolute Beginner Talk**.*

---

