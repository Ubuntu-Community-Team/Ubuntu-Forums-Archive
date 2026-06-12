---
title: "Issues with internet"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by seth-chandler-combs on 2014-02-17
None of my applications have access to the internet while I am connected to it. I am running off of a somewhat newly installed zorin 8 os And i am connected to the same wifi and hardwire as my xbox and phones so I know its not the internet something is just not giving the apps internet but another odd thing is that it will load certain web pages but only those that are related to ubuntu such as this one here. And the only app that seems to have access is the ubuntu one backup system. So please help I have online classes I need the internet for and if I dont finish its a 500 dollar fine

---

### Post by varunendra on 2014-02-19
Welcome to Ubuntu Forums !

> **seth-chandler-combs said:**
> I am running off of a somewhat newly installed **zorin 8 os**

Zorin may be Ubuntu based, but is definitely not Ubuntu and may differ a lot in certain aspects.

The problem you mentioned sounds like a firewall issue, but we Ubuntu users may not be able to help much with that since most of the potential helpers may not have any experience with Zorin. If your course is important and you need Ubuntu or Linux for it, install Ubuntu instead, or ask for help on Zorin's own forums.

That being said, you may check if the native firewall is enabled (assuming it is same as in Ubuntu). In a terminal, run the following command to check it -
```
sudo ufw status
```
The program "ufw" means "Ubuntu FireWall", so not sure if it even exists in Zorin or not.

---

