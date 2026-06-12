---
title: "how to isntall version-specific packages for python?"
date: 2011-08-18
forum: Programming Talk
---

### Post by v923z on 2011-08-18
Hi All,

How can I make apt-get install python packages for specific versions of python? My default is 2.6, and all packages are installed for that. I have python 2.7, and 3.2, and I would also like to get the packages for those versions. Is there a way to force apt-get to download, and install those?
Thanks,
Zoltán

---

### Post by ~!geek!~ on 2011-08-18
**Warning:** Do whatever you want but don't ever remove the python your machine is using. Python is essential for system to work. 
---------------------------------

Assuming you will take care of the above disclaimer, you can now download the python's specific versions available in the repository. It seems you are using 10.10, Just search for the python in synaptic manager and install it without removing any python you see already installed. No need to force your system to use a specific version you want to. 
Suppose you install python 3.2 using synaptic along with 2.6 (which you must not remove), you can now use different python interpretors using: > python3 command to launch python 3.2  or > python to launch default python i.e. 2.6 in your case and so on.

---

### Post by v923z on 2011-08-18
> **~!geek!~ said:**
> 
Suppose you install python 3.2 using synaptic along with 2.6 (which you must not remove), you can now use different python interpretors using:  command to launch python 3.2  or  to launch default python i.e. 2.6 in your case and so on.
Hi,

My problem is not that I could not install newer versions of python. As I said before, I have 2.6, 2.7, and 3.2, and my system works properly. The problem is that if I issue 
```

apt-get install python-numpy

```
then numpy will be installed for the default python version, 2.6. If I now want to use numpy with version 2.7, then when I try to import the module, python will complain that it is not installed. That is why I was thinking that perhaps I have to install numpy for 2.7, and 3.2, too. Is that really the case? If it is so, how can I instruct apt-get to get numpy for 2.7?
Zoltán

---

