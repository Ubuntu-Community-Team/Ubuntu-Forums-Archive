---
title: "g++: command not found...?"
date: 2006-02-01
forum: Programming Talk
---

### Post by twigboy on 2006-02-01
Hi everyone
I have been trying to compile some c++ code but am having an issue trying to get it to compile.  I have installed the GNU C++ compiler g++-4.0 from synaptic, is something else needed?
I am compiling with g++ -W -Wall - Werror <filename>.cc -o <filename>
Thanks

---

### Post by jrib on 2006-02-01
```
sudo apt-get install build-essential
```

The build-essential package will give you all the stuff you need to build stuff

---

### Post by twigboy on 2006-02-01
Sweet thanks a lot.  It worked like a champ.

---

