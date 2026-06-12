---
title: "gcda files not getting formed from gcov"
date: 2012-11-21
forum: Programming Talk
---

### Post by IAMTubby on 2012-11-21
Hi,
I understand this question is very specific to gcov, but I would like to go ahead and ask as I have been stuck for a long time. 

_**My scenario is as follows**_
1. My code contains an app folder and a lib folder. The lib folder contains a shared library called libcli.so
2. On building, gcno files are created for files both in the app and lib folder
3. This application is then run(executed) on a powerpc architecture.
4. On running, gcda files are created only for those source files which reside in the app folder, but not for those source files in the lib folder.
5. 
a) On executing gcov for a source file from within the app folder
_Assume that main.c exists within the app folder_
```

#gcov main.c
File '/home/projects/src/main.c'
Lines executed:61.19% of 67

```

b) On executing gcov for a source file from within the lib folder(constituent of libcli.so)
_Assume that getfile.c exists within the lib folder_
```

#gcov getfile.c
File '/home/projects/src/getfile.c'
Lines executed:0.00% of 27
/home/projects/src/getfile.c                                                                                       :creating 'getfile.c.gcov'
```
As you can see, it says 0.00% because the corresponding .gcda file is not created.

_**Common mistakes I have taken care of and learnt from other forums**_
1. Yes, I have run the executable in a way(with appropriate arguments) such that the code in getfile.c gets called.  
   I'm running the executable on the powerpc from a local folder. The .gcda files do not get created here for getfile.c     but main.gcda gets created here.
2. I have checked if the .gcda's are created in the .libs folder. No it's not.
3. I have created the same file chain on the target powerpc machine as is on the host machine where code was compiled in case it was expecting this path.
4. I have checked if I have write permission for the .libs folder. Yes I have.
5. I have flashed the libcli.so on the target PC.
6. I have added -fprofile-arcs --coverage on both the CFLAGS as well as LDFLAGS
My Makefiles in both the app as well as lib folder look as follows
```

CFLAGS+= -fprofile-arcs -ftest-coverage --coverage
LDFLAGS+= --cref --warn-common -shared -nostdlib -Wl,-Bsymbolic --fprofile-arcs
.
.
.
.
$(LIBFILE) : $(OBJS)
        $(LINK) $(LDFLAGS) /home/projects/toolchain/ppc_4xx/usr/lib/gcc/ppc-linux/4.2.2/libgcov.a \
                --retain-symbols-file,$(SYMFILE) \
                -Wl,-soname,$(LIBFILE) \
                -Wl,-Map,$(MAPFILE) \
                -o $@ \
                $(OBJS) \
                $(LIBS) /home/projects/toolchain/ppc_4xx/usr/lib/gcc/ppc-linux/4.2.2/libgcov.a

```
7.I didn't quite understand how to use these 2 environment variables. Please refer [http://gcc.gnu.org/onlinedocs/gcc/Cross_002dprofiling.html#Cross_002dprofiling](http://gcc.gnu.org/onlinedocs/gcc/Cross_002dprofiling.html#Cross_002dprofiling)


**_Some important paths_**
1. All the sources files on the x86 pc are on : /home/projects/map/src/cli
2. Code is getting built on the x86 pc from   : /home/projects/map/build/cli/lib/linux
3. I's running the executable on the powerpc from : /tmp(I have copied main.gcno and getfile.gcno here and have copied main.c and getfile.c into /home/projects/map/src/cli on the powerpc. (Yes I created the same path on the powerpc).


Please advise.

---

### Post by IAMTubby on 2012-11-22
Please note that I have also posted the question on gcc-help. 
I'm sorry for repeating the same question on multiple forums, as I was unware of gcc-help, and feel that since this question is more related to gcc/gcov, it would be a good idea.

In future, am I allowed to repeat the same question on multiple forums?

---

### Post by Bachstelze on 2012-11-22
> **IAMTubby said:**
> 
In future, am I allowed to repeat the same question on multiple forums?

There was no law against it last time I checked. And of course, the rules of this forum do not govern what you post elsewhere.

---

