---
title: "inernet issues with hardy heron broadcom"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-04-27
I'm sure this is getting redundant but if its any help im tying to install build essentials and Im gettin the following error message

 status: error wrong archetecture 'i386'

is it because Im running 64 bit?

help

---

### Post by frup on 2008-04-27
May I suggest a different title for your thread?
perhaps "wrong architecture error with build essential" or something like that.

---

### Post by Michael.Godawski on 2008-04-27
How do you install the build essential package? If you run in terminal:
```
sudo apt-get install build-essential
```
the correct version should be installed.

---

### Post by PatrickMoore on 2008-04-27
i have been trying to install i downloaded the 64bit version. when i enter:

 sudo aptitude install build-essential

 i get the error message "couldn't find any package whose name  or description matched build essential" no packages will be installed upgraded or removed

---

### Post by PatrickMoore on 2008-04-27
when i try the package installer i get
"error: dependancy is not satisfiable: libc6-dev libc-dev"

---

### Post by frup on 2008-04-27
Have you done some weird stuff with your repositories? I presume you already have your broadcom wireless working.

---

### Post by PatrickMoore on 2008-04-27
> **frup said:**
> Have you done some weird stuff with your repositories? I presume you already have your broadcom wireless working.

not that i know of. i installed  just yesterday i did try to establish a manual network connection. but thats it

---

### Post by PatrickMoore on 2008-04-27
the wireless only works when i boot into windows. it doesnt hve anything in ubuntu. my biggest issue is that im stuck on the installation prior to fwcutter

---

