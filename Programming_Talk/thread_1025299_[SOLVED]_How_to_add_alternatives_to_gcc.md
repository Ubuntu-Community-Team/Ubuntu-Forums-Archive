---
title: "[SOLVED] How to add alternatives to gcc?"
date: 2008-12-29
forum: Programming Talk
---

### Post by hecato on 2008-12-29
Hi there, ubuntu 8.10 come with gcc-4.3 but for a project I need gcc-4.2, so I installed it, the solution I found is 
```

After installation:
sudo rm -d /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.1 /usr/bin/gcc

This way your system will keep the gcc-4.3 but use by default gcc-4.1 .

If you need to go back to 4.3 :
sudo rm -d /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.3 /usr/bin/gcc
```

The problem is that I dont want to manage the sym links, I want to use

```
update-alternatives --config gcc
```
and
```
update-alternatives --config g++
```
But
```

$ update-alternatives --config gcc
There are no alternatives for gcc.
$ update-alternatives --config g++
There are no alternatives for g++.
```

So the question is, how do I use update-alternatives for manage this way the alternative versions of gcc and g++?

---

### Post by hecato on 2008-12-30
I found this info on the general questions forum, here [http://ubuntuforums.org/showthread.php?t=80145](http://ubuntuforums.org/showthread.php?t=80145)

---

