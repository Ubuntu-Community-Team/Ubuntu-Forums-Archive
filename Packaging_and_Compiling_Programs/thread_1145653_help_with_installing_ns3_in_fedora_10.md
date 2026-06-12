---
title: "help with installing ns3 in fedora 10"
date: 2009-05-01
forum: Packaging and Compiling Programs
---

### Post by mrdosa on 2009-05-01
I have been an ubuntu user but right now, but i am forced to use fedora by my school. I need help with installing ns3 on fedora. 
I keep getting this error even though i installed the latest error.

[root@Mrudula ns-3.4]# ./waf -d debug configure
Checking for program g++                 : not found 
Checking for program c++                 : not found 
Checking for program icpc                : not found 
Checking for program c++                 : not found 
Checking for program CC                  : not found 
neither COMPILER_CC nor COMPILER_CXX are defined; maybe the compiler_cc or compiler_cxx tool has not been configured yet?

---

### Post by wwbdd on 2010-01-15
Looks like you need to run

```
sudo apt-get install gcc g++ python python-dev
```

for the basic functionality.  If you want more features enabled see [the ns-3 installation wiki page]("http://http://www.nsnam.org/wiki/index.php/Installation#Ubuntu.2FDebian")

---

