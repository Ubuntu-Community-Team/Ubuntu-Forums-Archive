---
title: "Xubuntu Core"
date: 2017-01-13
forum: New to Ubuntu
---

### Post by raulwynn on 2017-01-13
Alright, so I am new to Linux in general and I find a lot of applications burdensome. I'm working on some data mining software and I got to thinking. I currently run Xubuntu but I want to strip it. What is the difference between Xubuntu and the "Core" version. Also, I am interested in stripping the Binti name so I can integrate the software I to the OS and if feasible, market it. Now I know the process will be rough but how would I go about stripping as much as possible from Xubuntu but keep the kernel and core filing system in tact.

In faith with hope,
Raulwynn

---

### Post by howefield on 2017-01-13
> **raulwynn said:**
> ... but how would I go about stripping as much as possible from Xubuntu but keep the kernel and core filing system in tact.

Start with a minimal install and then build on the packages that you want would probably be the ideal way to go. Basically building up rather than stripping down whether that's with xubuntu-core or even more granular is up to you.

[https://xubuntu.org/news/introducing-xubuntu-core/](https://xubuntu.org/news/introducing-xubuntu-core/)

---

### Post by geeksmith on 2017-01-13
You can strip Ubuntu (or Xubuntu, which is mostly Ubuntu with a lighter desktop environment) down until it's no longer considered Ubuntu at all. At that point, of course, you're less likely to find help if you have problems.

You can start by looking at the list of installed packages (dpkg --get-selections) and start removing those you don't need. Be careful -- you are going to break it at some point, so you ought to do this on a disposable installation, like a VM with a snapshot that you can revert to when you remove something you actually need.

As far as stripping out the name and every trace that this is an Ubuntu system...well...you can do whatever you want with it. You'll have to do some digging and learning beyond the scope of a discussion in this forum, I suspect.

You might want to look at debootstrap -- it may be easier to start with something ultra minimal and build it up, rather than start with something bigger and strip it down. (Edit -- yeah, what howefield said!)

---

