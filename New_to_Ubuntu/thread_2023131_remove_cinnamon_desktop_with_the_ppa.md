---
title: "remove cinnamon desktop with the ppa"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by krishnan t s k on 2012-07-12
A few weeks back i installed the cinnamon desktop in ubuntu through the ppa(i'm not able to find the link for adding the ppa now :( ) 
Now i want to remove the cinnamon desktop completely... Is there any way to do it? I tried to do it through synaptic but quit at the last minute as i didnt know if all packages were marked for removal
Thanks in advance :)

---

### Post by Krytarik on 2012-07-12
Presuming that you've installed Cinnamon the way as described [here]("http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop/94202#94202"), running these commands should be sufficient:
```
sudo apt-get install ppa-purge
sudo apt-get purge --auto-remove cinnamon
sudo apt-get autoremove
sudo ppa-purge ppa:gwendal-lebihan-dev/cinnamon-stable
```Note: The duplicate auto-removal is to remove as many residual packages as possible.

Regards.

---

### Post by krishnan t s k on 2012-07-12
thanks for the reply... yes thats the link i installed it from
the first 3 commands work to perfection on the sudo-ppa purge command, i get the follolwing
```
private@ubuntu:~$ sudo ppa-purge ppa:gwendal-lebihan-dev/cinnamon-stable
Updating packages lists
PPA to be removed: gwendal-lebihan-dev cinnamon-stable
Warning:  Could not find package list for PPA: gwendal-lebihan-dev 
cinnamon-stable

```The entry for cinnamon is removed from the log in screen however... what should i do now? And thanks a lot for your help :)

---

### Post by Krytarik on 2012-07-12
> **krishnan t s k said:**
> on the sudo-ppa purge command, i get the follolwing
```
private@ubuntu:~$ sudo ppa-purge ppa:gwendal-lebihan-dev/cinnamon-stable
Updating packages lists
PPA to be removed: gwendal-lebihan-dev cinnamon-stable
Warning:  Could not find package list for PPA: gwendal-lebihan-dev 
cinnamon-stable

```
Hmm, maybe it's already removed from your Software Sources, somehow - please check that. And if not, just remove it from there.

---

### Post by krishnan t s k on 2012-07-12
yes its now removed...thank you very much :):)

---

### Post by vasa1 on 2012-07-12
Very useful thread :)

I've bookmarked it and will refer people to it if need be.

---

