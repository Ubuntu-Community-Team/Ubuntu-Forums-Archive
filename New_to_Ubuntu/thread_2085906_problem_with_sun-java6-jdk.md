---
title: "problem with sun-java6-jdk"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by SchrodingerCat on 2012-11-19
Hi all,
i am trying to install Bluej on ubuntu 12.04. In the website i found out that first at all i have to install the sun-java6-jdk but 
after my input
```
sudo apt-get install sun-java6-jdk
```
this is the output

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate

```

how can i solve the problem?
thank you

---

### Post by Cheesemill on 2012-11-19
The official Java isn't allowed in the repositories any more ever since Oracle changed the licensing terms. There are 2 options available to you, either install Open JDK from the repositories or follow the steps [here]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") to install Oracle Java.

All of this information can be found on the Ubuntu Java wiki page:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by pkadeel on 2012-11-19
Oracle's original java jdk can not be installed via repository.

What you can do via repository is to use openjdk. It works in most of the cases.
Version 7 (latest)
```
sudo apt-get install openjdk-7-jdk
```

Version 6
```
sudo apt-get install openjdk-6-jdk
```

If you must use the original Oracle's JDK then use the link given in cheesemill's post.[]("https://help.ubuntu.com/community/Java")

---

