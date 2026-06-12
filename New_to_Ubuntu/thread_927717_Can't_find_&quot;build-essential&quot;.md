---
title: "Can't find &quot;build-essential&quot;"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Vampiree on 2008-09-23
When I type [COLOR="Red"][SIZE="6"]sudo apt-get install build-essential[/SIZE][/COLOR] :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

---

### Post by overdrank on 2008-09-23
> **Vampiree said:**
> When I type [COLOR="Red"][SIZE="2"]sudo apt-get install build-essential[/SIZE][/COLOR] :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

Hi and have you tried via synaptic manager also?
You may have to add some repositories
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by echo314 on 2008-09-23
Thats odd. I agree with the above post, look into what repositories you have enabled. If your CD you installed with is enabled, then you can try that command while the CD is in your drive.

---

### Post by cada on 2008-09-23
i agree also.
put in the cd you installed from.

if you are installing from the net, make your your connection is good.

if you don't succeed, look at System->administration->software sources

make sure the tick box for the cdrom/dvd is choosen or not, depending on whether you want to get the packages from the cdrom/dvd

---

### Post by decius6i5 on 2008-12-21
You have to run "apt-get update" first.

---

