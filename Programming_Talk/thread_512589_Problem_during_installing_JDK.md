---
title: "Problem during installing JDK"
date: 2007-07-29
forum: Programming Talk
---

### Post by treotan on 2007-07-29
Hi All,

I found a good link for introducing how to install jdk in ubuntu, but I can't success. I just follow the instruction ([http://my-ubuntu.blogspot.com/2005/12/sun-java-sdk-15.html](http://my-ubuntu.blogspot.com/2005/12/sun-java-sdk-15.html)).

root@tracking:/usr/local# sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
E: The package jdk needs to be reinstalled, but I can't find an archive for it.

Why I try to install something, it also prompt this msg?
root@server:/usr/local# sudo apt-get install fakeroot alien                                             
Reading package lists... Done
Building dependency tree... Done
E: The package jdk needs to be reinstalled, but I can't find an archive for it.

How I can fix it? Thanks.

Treo

---

### Post by angryfirelord on 2007-07-30
Enable your universe and multiverse repos.

Then, simply issue this command:
```
sudo apt-get install sun-java6-jdk sun-java6-fonts sun-java6-plugin
```

---

