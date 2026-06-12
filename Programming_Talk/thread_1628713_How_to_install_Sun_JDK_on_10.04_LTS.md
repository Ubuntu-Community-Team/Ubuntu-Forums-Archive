---
title: "How to install Sun JDK on 10.04 LTS"
date: 2010-11-23
forum: Programming Talk
---

### Post by mayanksh on 2010-11-23
Hi ,

  I have tried may ways that have been posted on this forum and many others to get sun-java6-jdk installed.

Problem :
=======

   sun-java6-jdk : depends on sun-java6-bin and sun-java6-jre

  and ...
  
  sun-java6-bin depends on sun-java6-jre
 
and ...
 
 sun-java6-jre depends on sun-java6-bin !!!! ( They are interdependent...this is as per ubuntu official site .. packages.ubuntu.com )

My Tries :
=======

Since the 2 packages sun-java6-bin and sun-java6-jre are interdependent I figured there is no way to forcefully or manually download and install it.

I tried :  sudo apt-get update  ... sudo apt-get install sun-java6-jdk

I tried adding the "cannonical partner " repository . 

My source.list file is :

 deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
 deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

 deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
 deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

 deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
 deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
 deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
 deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

 deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
 deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
 deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
 deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security main restricted
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security main restricted
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security universe
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security universe
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security multiverse
deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) lucid restricted universe main multiverse



Please help because it seems that since ubuntu has discontinued sun and placed open-jdk it looks like impossible to work with standard sun-jdk on ubuntu 10.04 LTS

thanks,
Mayank

---

### Post by lukeiamyourfather on 2010-11-23
> **mayanksh said:**
> 
Please help because it seems that since ubuntu has discontinued sun and placed open-jdk it looks like impossible to work with standard sun-jdk on ubuntu 10.04 LTS


This is not the case. I've installed the Sun JDK many times on 10.04 LTS. This is the line that really matters for the package sources.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

The package name is sun-java6-jdk, and it will install a bunch of other stuff with it. What does it say when you update and the install? Is it saying the package is not found, an error during install, details?

---

### Post by mayanksh on 2010-11-23
Thanks for the quick reply.

I think you can notice that in my source.list , the one line that you recommend is already present.

Any special reason for pointing it again ?

---

### Post by SecretCode on 2010-11-23
I think the reason for pointing out that line is to demonstrate that ubuntu has **not** dropped sun-java.

Also your reasoning around interdependencies being the problem isn't right - apt will just install both of them.

When you run 
```
sudo apt-get install sun-java6-jdk
```
what errors, exactly, do you get?

---

### Post by lukeiamyourfather on 2010-11-23
> **mayanksh said:**
> Thanks for the quick reply.

I think you can notice that in my source.list , the one line that you recommend is already present.

Any special reason for pointing it again ?

I'm saying it should work because you already have the correct sources. What error is it giving you? More information is needed to help you.

---

