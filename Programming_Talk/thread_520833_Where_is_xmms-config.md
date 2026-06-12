---
title: "Where is xmms-config?"
date: 2007-08-08
forum: Programming Talk
---

### Post by lduperval on 2007-08-08
Hi,

I'm trying to compile longplayer and it needs a copy of xmms-config. 

Where is that file located?

On a related note, how do I determine which package contains what file?

Thanks,

L

---

### Post by nitro_n2o on 2007-08-08
I'm not sure where to find it, but here are general hints: 
to find a file in your system use: 
```
locate <filename> 
```
or 
```
whereis <filename> 
```

for your second question (how to find which package contains wht) do 
```
apt-cache search <package_name>
```

good luck

---

### Post by lduperval on 2007-08-08
Thanks for the reply. I tried locate and even beagle to search for xmms-config somewhere, but I did not find it.

Does the apt-cache search look for packages that are installed already? How can I ask "what package installs a file called xmms-config"?

L

---

### Post by RedSquirrel on 2007-08-08
I would try installing the development package for xmms, which is called **xmms-dev**.

---

