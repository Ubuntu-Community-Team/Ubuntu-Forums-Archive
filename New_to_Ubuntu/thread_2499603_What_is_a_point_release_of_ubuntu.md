---
title: "What is a point release of ubuntu ??"
date: 2024-08-02
forum: New to Ubuntu
---

### Post by enigma20100 on 2024-08-02
I heard some people say  wait for the 24.04,1 release before installing.. what is that?  and when will it be released ?

---

### Post by yancek on 2024-08-02
I don't see a specific date on the Ubuntu site but it will be this month.

[https://help.ubuntu.com/community/NobleUpgrades/](https://help.ubuntu.com/community/NobleUpgrades/)

---

### Post by oldfred on 2024-08-02
See Future in this one.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

And then you get into Enablelement stack.
The original release & first point release use the same kernel. That is for stability. And unless system new do not need but can update to newer 
But since supported for 5 years, newer hardware will need newer kernel & drivers, so .2 and beyond will automatically update to the latest kernel.

[https://en.wikipedia.org/wiki/Ubuntu_version_history](https://en.wikipedia.org/wiki/Ubuntu_version_history)

---

### Post by sunday28 on 2024-08-02
> **enigma20100 said:**
> I heard some people say  wait for the 24.04,1 release before installing.. what is that?  and when will it be released ?

This is recommended when upgrading from LTS to LTS.
That is, if you currently have Ubuntu 22.04 installed, the update to 24.04 is not yet available.
You will be notified when you exit on 24.04.01.
If you are performing a new installation, then you do not need to wait for .01.
It is also worth updating from 23.10.
Especially since this version has already reached its EOL.
.01 will be August, 15.

---

### Post by guiverc on 2024-08-02
> **enigma20100 said:**
> I heard some people say  wait for the 24.04,1 release before installing.. what is that?  and when will it be released ?

I post *point release* announcements to the fridge.. and will give a quote from 22.04.2

[https://fridge.ubuntu.com/2024/02/22/ubuntu-22-04-4-lts-released/](https://fridge.ubuntu.com/2024/02/22/ubuntu-22-04-4-lts-released/)

> 
As usual, this point release includes many updates and updated  installation media has been provided so that fewer updates will need to  be downloaded after installation. These include security updates and  corrections for other high-severity bugs, with a focus on maintaining  stability and compatibility with Ubuntu 22.04 LTS. 

ie. "***updated  installation media has been provided so that fewer updates will need to  be downloaded after installation***"

There can be differences with some media; eg. Ubuntu *flavors* at the initial (.0) & .1 release will still have the GA kernel stack on install media, but .2 & later will have the HWE kernel stack... 

Example using Lubuntu means 22.04 & 22.04.1 ISO  had the 5.15 kernel, where 22.04.2 had 5.19, 22.04.3 had 6.2, 22.04.4 had 6.5 & 22.04.5 will have 6.8... This different kernel on ISO would update according to package on media; 22.04 & 22.04.1 using GA kernel package would remain 5.15 for the life of the system, where 22.04.2 & later media would upgrade meaning all current media still has 6.5 (6.8 is is still in *jammy-proposed*) so won't yet install.

```
linux-image-generic-hwe-22.04      | 6.8.0-40.40~22.04.3 | jammy-proposed | amd64, arm64, armhf, ppc64el, s390x

```
The new *point *media can cause different package defaults... where I'm using the kernel stack is an example...  The default can easily be changed post-install anyway by following the documentation if required....

If you want to see when an ISO is released; read the release schedule; for *noble* or 24.04 it can be seen at [https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649](https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649)

---

### Post by sports fan Matt on 2024-08-11
I just  upgraded to jammy myself And I see no need to upgrade to Noble yet. 

As I get older, if it ain’t broke, I’m not fixing it.

---

### Post by TheFu on 2024-08-11
> **sports fan Matt said:**
>  As I get older, if it ain’t broke, I’m not fixing it.

In general, I agree, except that when a release is losing support, I want/need to update to a supported release at least 1 month before the older release support ends completely.  Sometimes there are problems that might take a few weeks for me to figure out when life is happening completely unrelated to computers.

Never run a release that isn't supported.  It harms not just you, but the rest of the world.

---

