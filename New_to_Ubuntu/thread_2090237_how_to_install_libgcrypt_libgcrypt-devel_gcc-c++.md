---
title: "how to install libgcrypt libgcrypt-devel gcc-c++"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by msm25 on 2012-12-01
Hello,
 
This command is for centos, how can I install this on a ubuntu server?
 
yum install libgcrypt libgcrypt-devel gcc-c++
 
Thank you

---

### Post by Cheesemill on 2012-12-01
Try
```
sudo apt-get install libgcrypt libgcrypt-devel gcc-c++
```

---

### Post by msm25 on 2012-12-01
this was the result:
 
# sudo apt-get install libgcrypt libgcrypt-devel gcc-c++
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package libgcrypt
E: Unable to locate package libgcrypt-devel
E: Unable to locate package gcc-c+
E: Couldn't find any package by regex 'gcc-c+'
#

---

### Post by Cheesemill on 2012-12-01
You will have to search for the names of the equivalent packages in Ubuntu.

---

### Post by msm25 on 2012-12-01
> **Cheesemill said:**
> You will have to search for the names of the equivalent packages in Ubuntu.
 
Yes I did tried before I made this post, but I ended up to install the wrong packages, that is why I have made this post, to try to see if someone with more experience can help me.

---

### Post by Cheesemill on 2012-12-01
How about:
```
sudo apt-get install libgcrypt11 libgcrypt11-dev gcc
```

What software are you trying to compile? There may be an easier way to install all of the dependencies.

---

### Post by msm25 on 2012-12-01
Cheesemill,
 
Thank you so much for your help, your solution solved my problem. I did google for almost all combinations possible to get the solution but I wasn't able to find it. 
 
Can I ask you, what did you made the search of the names of the package, did you used google? How did you find that gcc-c++ was the gcc only?
 
Thank you again!

---

### Post by msm25 on 2012-12-01
> **Cheesemill said:**
> How about:
```
sudo apt-get install libgcrypt11 libgcrypt11-dev gcc
```
 
What software are you trying to compile? There may be an easier way to install all of the dependencies.
 
Hi,
 
it was the FreeRADIUS Plugin to generate the radiusplugin.so file , your solution did work :)

---

### Post by Cheesemill on 2012-12-01
> **msm25 said:**
> Can I ask you, what did you made the search of the names of the package, did you used google? How did you find that gcc-c++ was the gcc only?

No, I didn't use Google.

For the first 2 I searched the [Ubuntu package database]("http://packages.ubuntu.com/") for libgcrypt.
Gcc is a common package that I already knew about.

---

### Post by msm25 on 2012-12-02
> **Cheesemill said:**
> No, I didn't use Google.
 
For the first 2 I searched the [Ubuntu package database]("http://packages.ubuntu.com/") for libgcrypt.
Gcc is a common paackage that I already knew about.
 
 
Thank you Cheesemill !!!

---

