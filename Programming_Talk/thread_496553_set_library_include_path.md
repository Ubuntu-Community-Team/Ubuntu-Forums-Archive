---
title: "set library include path"
date: 2007-07-09
forum: Programming Talk
---

### Post by wayanwolvie on 2007-07-09
Dear all,

I have a problem. I have some library files in /home/ddd/mylibs/ . And I want to compile a program from another directory such that the  compiler (g++) will automatically include my library files. But I don't know how to set the library include path in linux environment. Can anybody help me please

---

### Post by meatpan on 2007-07-09
If you want the compiler to search a specific directory for libraries, use the '-L' option.  For example,  g++ -L/home/ddd/mylibs

Now, if you use the lower-case L option, the compiler will search /home/ddd/mylibs for the library name.  So if you have a lib 'libmylib.so' in /home/ddd/mylibs,  you could now run 'g++ -L/home/ddd/mylibs -lmylib' and the linking should include libmylib.so.

If you find that you are frequently using the -L option, check out the command ldconfig, or consider setting the environment variable 'LD_LIBRARY_PATH'. 

Does that help?

---

### Post by wayanwolvie on 2007-07-10
How to set the environment variable? 
Sorry, I am quite new on this matter

---

### Post by amo-ej1 on 2007-07-10
You could also check *man ldconfig* so you could (temporary) add a directory to the library search path using:

```

sudo ldconfig /path/to/my/usr/local/lib/

```

Use *ldconfig -p* to print out all libraries (and their location) in the library search path

---

### Post by jespdj on 2007-07-10
> **wayanwolvie said:**
> How to set the environment variable? 
Sorry, I am quite new on this matter
```
export LD_LIBRARY_PATH=/home/ddd/mylibs
```

---

### Post by stewienbrian on 2010-11-13
> **amo-ej1 said:**
> You could also check *man ldconfig* so you could (temporary) add a directory to the library search path using:

```

sudo ldconfig /path/to/my/usr/local/lib/

```

Use *ldconfig -p* to print out all libraries (and their location) in the library search path

thanks, this worked. however how to remove a directory in case we don't need it anymore ?

---

### Post by dapayne12 on 2011-01-31
Hi,

I'm not sure if this is too late to respond or not.  Or it may help the next person.

I just downloaded the same program and ran into the same problem.  However, I noticed libfmodex64.so was included in the install directory.  I then found a script ts3client_runscript.sh that takes care of the library path for the user.  I made my Custom Application Launcher point to that and had no problems.

David

---

