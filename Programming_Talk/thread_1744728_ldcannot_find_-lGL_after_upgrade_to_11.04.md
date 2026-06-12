---
title: "ld||cannot find -lGL| after upgrade to 11.04"
date: 2011-04-30
forum: Programming Talk
---

### Post by trollger on 2011-04-30
hi everyone.
 I have been programming an OGRE project on Ubuntu 10.04 for some time now and yesterday I upgraded to 11.04. Now My CodeBlocks project complains:

```

ld||cannot find -lGL|

```All the other libraries appear to work OGRE,CEGUI,OIS, and ODE all work.

I installed a driver and I have a working desktop so I am pretty sure it is safe to say openGL is somewhere on my computer. Is there a difference between Ubuntu 10 and 11 when it comes to this matter? any one have a solution?

---

### Post by trollger on 2011-04-30
Anyone? Should be an easy fix

---

### Post by maverick280857 on 2011-05-24
I have the same problem, trying to compile CUDA SDK examples. In 10.10 Maverick Meerkat, it was possible to fix all this using

```
sudo apt-get install freeglut3 freeglut3-dev
sudo apt-get install libxi libxi-dev  // **This** no longer works!
sudo apt-get install libxmu6 libxmu-dev
```

---

### Post by maverick280857 on 2011-05-24
Found a fix at [http://ubuntuforums.org/showpost.php?p=9285386&postcount=2](http://ubuntuforums.org/showpost.php?p=9285386&postcount=2)

```
sudo ln -s /usr/lib/libGL.so.xx.xx.xx /usr/lib/libGL.so
```

This is what ```
ls -l /usr/lib/libGL.so*
``` yields on my system:

```

lrwxrwxrwx 1 root root      27 2011-05-25 03:50 libGL.so -> /usr/lib/libGL.so.270.41.06
lrwxrwxrwx 1 root root      18 2011-05-05 14:20 libGL.so.1 -> libGL.so.270.41.06
-rwxr-xr-x 1 root root 1008272 2011-05-05 14:20 libGL.so.270.41.06

```

Hope this helps.

---

### Post by salemboot on 2011-06-02
Did anyone submit a bug report?

---

### Post by Qdoba on 2012-01-05
> **maverick280857 said:**
> Found a fix at [http://ubuntuforums.org/showpost.php?p=9285386&postcount=2](http://ubuntuforums.org/showpost.php?p=9285386&postcount=2)

```
sudo ln -s /usr/lib/libGL.so.xx.xx.xx /usr/lib/libGL.so
```This is what ```
ls -l /usr/lib/libGL.so*
``` yields on my system:

```

lrwxrwxrwx 1 root root      27 2011-05-25 03:50 libGL.so -> /usr/lib/libGL.so.270.41.06
lrwxrwxrwx 1 root root      18 2011-05-05 14:20 libGL.so.1 -> libGL.so.270.41.06
-rwxr-xr-x 1 root root 1008272 2011-05-05 14:20 libGL.so.270.41.06

```Hope this helps.

Just to clarify, you need to find the library you actually have (in this case libGL.so.270.41.06 and **force link** to that. So in this case it would be:

```
 sudo ln -s **-f** /usr/lib/libGL.so.270.41.06 /usr/lib/libGL.so

```Do a  ```
ls -l /usr/lib/libGL.so*
``` on your system to find the right one. And then afterwards the link should be [COLOR=Cyan]blue[/COLOR]->[COLOR=YellowGreen]green[/COLOR] colors instead of [COLOR=Red]red [/COLOR](red means broken link). Thank you Maverick!

---

### Post by MadCow108 on 2012-01-05
this is terrible advice.
You should never touch anything the package manager manages under /usr (excluding /usr/local)

the libGL.so symlink is provided by libgl1-mesa-dev
see [http://packages.ubuntu.com/search?searchon=contents&keywords=libGL.so&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libGL.so&mode=exactfilename&suite=natty&arch=any)
note this is just the symlink for linking. It is only needed during buildtime has nothing to with which library is used at runtime.

the  actually used library GL is managed via the alternatives system and depends on your graphics card and driver.
To change it do:
```
update-alternatives --config gl_conf
# or if its multiarched
update-alternatives --config $(dpkg-architecture -qDEB_HOST_MULTIARCH)_gl_conf
```
or use the gui galternatives.

---

