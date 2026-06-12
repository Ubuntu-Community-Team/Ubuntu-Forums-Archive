---
title: "liba53"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by usama2 on 2013-10-05
i am using ubuntu 12.04. i am trying to intall a software for which i  needed to install liba53. tell me that how can i install liba53

---

### Post by Frogs Hair on 2013-10-05
Hello and Welcome

If the library is available from the 12,04 repository try the following. ```
sudo apt get install liba53
``` If you are getting a message that is missing it is not available.I get no results for a package by that name from Ubuntu package search and it is not in the 13.04 repository if that is the complete name. 

  [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by usama2 on 2013-10-05
thnxx for the reply
i already tried this command but it says: E: Unable to locate package liba53

---

### Post by philinux on 2013-10-05
The only package that comes close to that is.

**liba52-0.7.4 **
(0.7.4-16build1) [universe]
 library for decoding ATSC A/52 streams. That package is already installed on my system. (saucy)

What software are you trying to install?

---

### Post by Frogs Hair on 2013-10-05
Check the package search link above . I didn't get a result when I searched and find nothing at the link below either , so make sure the package name is correct . What software are you trying to install ?



 [http://search.debian.org/cgi-bin/omega?DB=en&P=liba53](http://search.debian.org/cgi-bin/omega?DB=en&P=liba53)

---

### Post by usama2 on 2013-10-11
i am installing openbts

---

### Post by mc4man on 2013-10-11
Have no idea on how you're trying to install openbts but if you were to read here, under "Required Libraries/Utilities" you'll see where it says - 
 > You will also need to install liba53, which is included with the distribution. The following commands should install it correctly from the OPENBTS_ROOT

cd a53/trunk
sudo make install

Meaning a53 is included in the source, you build & install it yourself.

[http://wush.net/trac/rangepublic/wiki/BuildInstallRun](http://wush.net/trac/rangepublic/wiki/BuildInstallRun)

---

### Post by usama2 on 2013-10-11
yes i am following the same procedure as listed there. i entered that command but it did not worked. i am new to ubuntu and dont know how to fix this. here is the output of this command

usama@usama-Inspiron-N5110:~$ cd a53/trunk
bash: cd: a53/trunk: No such file or directory

---

### Post by VMC on 2013-10-11
> **usama2 said:**
> yes i am following the same procedure as listed there. i entered that command but it did not worked. i am new to ubuntu and dont know how to fix this. here is the output of this command

usama@usama-Inspiron-N5110:~$ cd a53/trunk
bash: cd: a53/trunk: No such file or directory
That means your either not in the correct hierarchy or the "a53" directory is somewhere else.

what does 'ls' show from the dir your working in.

---

