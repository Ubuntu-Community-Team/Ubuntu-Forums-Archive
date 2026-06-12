---
title: "No rule to make target fix???"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by rbcl15 on 2008-05-11
Hello

Has anyone found a fix for the above bug? I've been looking around and tried a few adjustments but am still awaiting breakthrough with this. There are a few packages I'd like to install but for this obstacle.

---

### Post by rbcl15 on 2008-05-11
Any suggestions for this it's been a few weeks? Would the 64-bit version of ubuntu 8.04 be any different?

---

### Post by rbcl15 on 2008-05-16
Is there any standard fix for this yet??? I'll look around again.

---

### Post by Oldsoldier2003 on 2008-05-16
> **rbcl15 said:**
> Is there any standard fix for this yet??? I'll look around again.

That error usually indicates you don't have all the dependencies installed.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
sudo apt-get build-dep <package_you_want_to compile>
```

apt-get build-dep only works for packages that reside in the repos already. So if it errors out, check the documentation for the package and install the build deps separately.

---

