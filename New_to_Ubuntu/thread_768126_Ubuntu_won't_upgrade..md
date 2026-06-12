---
title: "Ubuntu won't upgrade."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by EleFlameMax on 2008-04-26
I tried clicking "check" on the update manager, but it won't show that there's been a new distro. I tried sudo update, and click check like a million times.

---

### Post by zvacet on 2008-04-26
Just to be sure your system is up-to-date run 

```
sudo apt-get update && sudo apt-get upgrade
```
 After that try again with update manager.

---

### Post by EleFlameMax on 2008-04-30
> **zvacet said:**
> Just to be sure your system is up-to-date run 

```
sudo apt-get update && sudo apt-get upgrade
```
 After that try again with update manager.

It's still not working. I know that as a Linux user, I'm supposed to take a lot of crap from my machine, but this is getting fricking ridiculous.

---

### Post by shad0w_walker on 2008-04-30
More information is a good thing. Does the check button actually do anything such as pop up a window showing the progress of the check? Did the commands you tried produce any errors or anything weird?

---

### Post by EleFlameMax on 2008-04-30
> **shad0w_walker said:**
> More information is a good thing. Does the check button actually do anything such as pop up a window showing the progress of the check? Did the commands you tried produce any errors or anything weird?

1. Yes 

2. Nope.

---

### Post by Mahmoud on 2008-04-30
try:  Press Alt-F2 and type gksu "update-manager -d"

---

### Post by EleFlameMax on 2008-04-30
> **Mahmoud said:**
> try:  Press Alt-F2 and type gksu "update-manager -d"

And still, to no avail. DAMNBLINGS!

---

### Post by shad0w_walker on 2008-04-30
It's not the most direct way to do things but you could download the alternate Ubuntu install CD which has an upgrade script on it.

---

### Post by ff8ff8 on 2008-04-30
sort of a similar problem here, update manager and apt-get update don't show new updates on any server.
try reinstalling it in synaptic manager

---

### Post by sav2005 on 2008-05-02
I have the same problem. I have tried reinstalling all the update-manager and upadet-manager-core files with Synaptic, run update-manager, clicked check, rebooted, tried again! 

No luck. Meanwhile my laptop is happily but slowly (12 hours) upgrading Gutsy to Hardy. Why does Update-Manager work on some machines and not others?

---

### Post by sav2005 on 2008-05-02
I have the same problem. I have tried reinstalling all the update-manager and update-manager-core files with Synaptic, run update-manager, clicked check, rebooted, tried again! 

Yes, I have tried gksudo "update-manager -c -d".

No luck. Meanwhile my laptop is happily but slowly (12 hours) upgrading Gutsy to Hardy. Why does Update-Manager work on some machines and not others?

---

