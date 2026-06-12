---
title: "how to install gcc"
date: 2014-04-03
forum: Packaging and Compiling Programs
---

### Post by chkay_chtemp on 2014-04-03
hi please me help with the following questions

1)how to install all gcc related packages?

2) I see libc6* packages named as "embedded gnu c library"(in synaptic package manager) which means they are not for normal programing 
then what is the package for standard c library

3)how to know the default "include" and "lib" search paths for gcc

---

### Post by Warren Hill on 2014-04-03
1. Most people need more than just gcc

```
sudo apt-get install build-essential
```

Should install most of what you need

2. Not Sure

3 See here [GCC Search Path]("http://stackoverflow.com/questions/1217943/where-are-include-files-stored-ubuntu-linux-gcc")

---

### Post by chkay_chtemp on 2014-04-03
thank you

---

