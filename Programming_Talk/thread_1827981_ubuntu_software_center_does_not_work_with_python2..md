---
title: "ubuntu software center does not work with python2.7"
date: 2011-08-18
forum: Programming Talk
---

### Post by v923z on 2011-08-18
Hi All,

I was wondering whether someone could tell me how I could upgrade my python installation. As it turns out, I have python2.6, python2.7, and python3.2 installed, and all installations work properly, if I invoke them. At present, python2.6 is the default python on my system. I would really need 2.7, but when I make the symbolic link in /usr/bin point to python2.7, Ubuntu's software center stops working. Is there a way to fix this problem? I am running Maverick Meerkat on a 64-bit computer. 
Thanks,
Zoltán

---

### Post by cgroza on 2011-08-18
Could you run this at the command line and post the output:
```

ubuntu-software-center

```It should give us a hint why it isn't working.
I am running python2.7 in Natty and ubuntu-software-center works fine here.

---

### Post by v923z on 2011-08-19
> **cgroza said:**
> Could you run this at the command line and post the output:
```

ubuntu-software-center

```It should give us a hint why it isn't working.
I am running python2.7 in Natty and ubuntu-software-center works fine here.

Hi,

Thanks for the reply! Here is the output of the command line command
```

v923z@penguin:h5py-2.0.0$ software-center 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    import pygtk
ImportError: No module named pygtk

```Then it is simply that python2.7 can't find the gtk bindings. In fact, I have already asked this question in another thread [http://ubuntuforums.org/showthread.php?t=1828108](http://ubuntuforums.org/showthread.php?t=1828108)
What would be the answer to the question posed there? (I don't want to repeat it here, because that would probably count as cross-posting.)
Thanks,
Zoltán

---

### Post by Bachstelze on 2011-08-19
There is no straightforward way that I know of to do what you want to do. One slightly cumbersome way would be to reinstall the module from source against your PYthon version of choise.

Whatever you do, **never** change the default Python version. If you really wnt to, you will have to use another distro.

---

### Post by v923z on 2011-08-19
> **Bachstelze said:**
> There is no straightforward way that I know of to do what you want to do. 

That is really odd: that would basically mean that one can use only one python distribution, the rest would be useless, unless you go through the trouble of installing everything from source.
Zoltán

---

### Post by MadCow108 on 2011-08-19
> **v923z said:**
> That is really odd: that would basically mean that one can use only one python distribution, the rest would be useless, unless you go through the trouble of installing everything from source.
Zoltán

a distribution cannot support every old and future version of python.
It is built and tested with one default and sometimes one optional version and will stick to that during its support time.

If you need python2.7 as default you have to update to natty, because only there you can be quite sure that most software will also work with it (although the transition is still not fully complete and will probably still take a while)

For your own software you can use whatever python version you wish, but you may have to install it yourself.

---

### Post by v923z on 2011-08-19
> **MadCow108 said:**
> a distribution cannot support every old and future version of python.
It is built and tested with one default and sometimes one optional version and will stick to that during its support time.

That is OK, and I have absolutely no problems with using python2.6 as the default. However, I would expect that if I issue "python2.7" on the command line, and get into a python2.7 session, then I should be able to use all modules. After all, at this point, python2.7 is just another software, and it has nothing to do with the system comman "python", for that is linked to 2.6. So, I don't really understand why it is not possible to just install the modules for each version of python using apt-get, and then depending on which version you are running in a particular case, let python find the module. Again, the problem is that I have numpy, e.g., but that is installed in the python2.6 folders, therefore, python2.7 won't find them. (And even if it did, it might not be compatible with it.)
Zoltán

---

### Post by MadCow108 on 2011-08-19
from maverick onwards you should have all packages installed with 2.7 modules.

in lucid you should be able to run some modules installed for 2.6 with 2.7 by doing this:
```
PYTHONPATH=/usr/lib/python2.6/dist-packages python2.7
```

numpy will probably not work like this, it may need to be recompiled against 2.7

---

### Post by Bachstelze on 2011-08-19
> **v923z said:**
>  So, I don't really understand why it is not possible to just install the modules for each version of python using apt-get,

As MadCow said, they can't support everything. If you want the packages to be available through Apt, it means someone has to build, test and upload them. Maybe they just don't have the manpower. Why don't you ask that to the relevant people (and offer your help if the problem is really lack of manpower) instead of whining here?

---

