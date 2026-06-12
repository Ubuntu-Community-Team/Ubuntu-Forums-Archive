---
title: "Update to 12.04 Beta1 risky?"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by kramer65 on 2012-02-24
Hello,


I've been running Ubuntu 10.04 for almost two years now and I am really happy with it. For a recent project however, I need to use Python version 2.7, which is not in the repositories. There are apparently [ways]("http://askubuntu.com/questions/4967/whats-the-best-way-to-get-python-2-5-and-2-7-on-ubuntu-10-04#4984") to get python 2.7 on Ubuntu 10.04, but these do not include any packages (which I heavily use), and according to [this thread]("http://ubuntuforums.org/showthread.php?t=1529315") other python versions might also terribly break the total Ubuntu installation. I am running some tests for the project in a virtualbox installation with Ubuntu 11.10 now, but unfortunately my computer constantly freezes, which I think is caused by virtualbox.

Since I do value stability a lot I am eagerly waiting for Ubuntu 12.04 to come out. Since I cannot wait for too long with starting this project I thought of installing the first beta of Ubuntu 12.04 next week (1st of March). 

My question is: how risky is this? I know that it is a beta and it shouldn't be used on production machines. But seeing that it is an LTS release I guess they want to make it as stable as possible, which I hope already has an influence on the stability of the development releases. If I install this beta1 and from there on upgrade to the major 12.04 release, is it the same as installing a fresh 12.04 installation? If beta1 runs fine, how many things will still change between beta1 and the final release?

In general: would you think this is a good idea?

---

### Post by unibroker on 2012-02-24
I downloaded 12.04 last night from 11.10.  In the very short time I've been using it I would say it is far from stable.  Nothing major but from the boot up (a lot longer than 11.10) to just navigating around the desktop I definitely know that I'm on a beta version.

> **kramer65 said:**
> Hello,


I've been running Ubuntu 10.04 for almost two years now and I am really happy with it. For a recent project however, I need to use Python version 2.7, which is not in the repositories. There are apparently [ways]("http://askubuntu.com/questions/4967/whats-the-best-way-to-get-python-2-5-and-2-7-on-ubuntu-10-04#4984") to get python 2.7 on Ubuntu 10.04, but these do not include any packages (which I heavily use), and according to [this thread]("http://ubuntuforums.org/showthread.php?t=1529315") other python versions might also terribly break the total Ubuntu installation. I am running some tests for the project in a virtualbox installation with Ubuntu 11.10 now, but unfortunately my computer constantly freezes, which I think is caused by virtualbox.

Since I do value stability a lot I am eagerly waiting for Ubuntu 12.04 to come out. Since I cannot wait for too long with starting this project I thought of installing the first beta of Ubuntu 12.04 next week (1st of March). 

My question is: how risky is this? I know that it is a beta and it shouldn't be used on production machines. But seeing that it is an LTS release I guess they want to make it as stable as possible, which I hope already has an influence on the stability of the development releases. If I install this beta1 and from there on upgrade to the major 12.04 release, is it the same as installing a fresh 12.04 installation? If beta1 runs fine, how many things will still change between beta1 and the final release?

In general: would you think this is a good idea?

---

### Post by grahammechanical on 2012-02-24
Why don't you dual boot? That is what I am doing right now with 12.04 and I have been using it since before it was alpha 1 and I find it very stable. I have been using it as my daily working Ubuntu instead of my 11.10 Ubuntu. That is how stable it is.

I have done one re-install in that time and that was down to my experimentation and a desire for an easy fix.

In 12.04 were are now at the point where new features cannot be added as all the effort has to be put into fixing things and not possibly creating new problems.

A new feature of this development cycle has been inviting those haunting the Ubuntu+1 section of this forum to do some specific testing before the package was put into 12.04. So, I shared in testing Unity 5, Unity 5.4 and Unity 5.4 + HUD before they were put out as updates.

Doing a daily update will bring 12.04 beta to 12.04 distribution release. As always protect your data by having it on a separate /home partition.

In May I will download the 12.04 iso image and use it to do a fresh install over my 11.10 and also this 12.04 development branch just to clear out any possible settings conflicts. Then I will switch to 12.10. I expect that to be very stable because most of the big changes have already been made by then.

Regards.

---

### Post by Mark Phelps on 2012-02-24
In general, upgrading to ANY pre-release version is risky.

The closer you are to the actual release, the less risk, but since there is no easy way to roll-back to the working version you have now,  upgrading is taking the risk you end up with an unstable or nonworking setup.

---

### Post by JRV on 2012-02-24
I suspect there will be problems with the upgrade from 10.04 to 12.04.  The change from Gnome 2 to Unity is huge, as is the change from gtk2 to gtk3.  I am not going to risk it.  I will be doing a fresh install after it is released.  I don't let pre-release code anywhere near my main system.

---

### Post by sudodus on 2012-02-24
> **grahammechanical said:**
> Why don't you dual boot? That is what I am doing right now with 12.04 ...
+1
Dual boot and use 12.04 when you need it (Python version 2.7 and maybe other new software). Keep 10.04 at least until 12.04 is officially released.

---

### Post by Zill on 2012-02-24
> **kramer65 said:**
> ...Since I do value stability a lot I am eagerly waiting for Ubuntu 12.04 to come out...
Although 12.04 will be an LTS release, this does not really indicate that it will *initially* be "stable".  IMHO, *all* Ubuntu releases are, at first, betas and it takes time for the bugs to be ironed-out.  The main advantage of an LTS is that there is far longer for it to settle down and ensure that any significant bugs get squashed.

So, my view is that if you want stability, do not install *any* release immediately it comes out but wait several weeks, or even months, before installing.  If you do this with an LTS release such as 12.04 this will then give you a stable and reliable system until [April 2017]("https://wiki.ubuntu.com/Releases").

---

