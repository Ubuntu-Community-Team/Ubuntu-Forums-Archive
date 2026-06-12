---
title: "finding recently installed apps in ubuntu 11.10"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by zfolwick on 2012-01-06
hello,

I'm trying to install sage computing software from:[http://boxen.math.washington.edu/sage/linux/32bit/index.html](http://boxen.math.washington.edu/sage/linux/32bit/index.html)

I followed (one of the many different) installation instructions:
"
2. Extract the tarball:

       tar -xvf sage-*.tar

3. cd into the Sage directory and type make:

       cd sage-*/
       make
"

but can't find the program.  I had the same problem when I installed chromium browser- but somehow accidentally found it.  Is there a way to find apps in the unity interface?

---

### Post by Frogs Hair on 2012-01-06
If you have the Synaptic Package Manager installed you can find out if the package is installed  . Use the following command to find the folder location .```
whereis program name
```

The program at the posted link is Ubuntu 10.04 compatible , will it work on 11.10 / Gnome 3 or do you have a newer package installed ?

---

### Post by Frogs Hair on 2012-01-06
If you want a list everything in the form of a text document run the following command and you will find a list in your home folder . Look at the list not the terminal output . ```
dpkg --get-selections > apps.txt

```

---

