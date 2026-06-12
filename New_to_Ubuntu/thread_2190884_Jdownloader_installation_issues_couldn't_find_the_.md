---
title: "Jdownloader installation issues couldn't find the package jdownloader"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by metalbuddha on 2013-11-29
I've been reading through the similar posts which were solved but couldn't really get my jdownloader to work.

Following is the background

I use 
sudo add-apt-repository ppa:jd-team/jdownloader
sudo apt-get update && sudo apt-get install jdownloader

and get 

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package jdownloader
che@che-laptop:~$

Any ideas why it can't find the package

any help would be much appreciated

Cheers

---

### Post by overdrank on 2013-11-29
Hi and welcome the commands are  I believe
```
sudo add-apt-repository ppa:jd-team/jdownloader
sudo apt-get update
sudo apt-get install jdownloader-installer
```
Found here
[https://launchpad.net/~jd-team/+archive/jdownloader](https://launchpad.net/~jd-team/+archive/jdownloader)

---

