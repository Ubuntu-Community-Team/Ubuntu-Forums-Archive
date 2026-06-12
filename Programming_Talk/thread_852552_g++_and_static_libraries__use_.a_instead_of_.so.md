---
title: "g++ and static libraries / use .a instead of .so"
date: 2008-07-07
forum: Programming Talk
---

### Post by Cygnus on 2008-07-07
Hi. I have a minor problem. Do you know how to make g++ -l flags use the .a library instead of the .so ones when both are available ? Hardcoding the path works fine, but I assume there is a better way.

In short; if you have liba.so and liba.a and specify -la to g++ it seems to pick up liba.so. Can you make it prefer .a instead ?

---

### Post by LaRoza on 2008-07-07
> **Cygnus said:**
> Hi. I have a minor problem. Do you know how to make g++ -l flags use the .a library instead of the .so ones when both are available ? Hardcoding the path works fine, but I assume there is a better way.

In short; if you have liba.so and liba.a and specify -la to g++ it seems to pick up liba.so. Can you make it prefer .a instead ?

.a is for static linking and .so is for shared libraries.

Look up on how to static link (man gcc)

---

### Post by Cygnus on 2008-07-07
> **LaRoza said:**
> .a is for static linking and .so is for shared libraries.

Look up on how to static link (man gcc)

The static linking works fine when using full path to the .a file, I just want to know if there is a flag or setting to make use static linking of a library when you use -l and there are are both .so and .a versions available.

I have already looked in man gcc of course but not yet found anything.

---

### Post by gnusci on 2008-07-07
If the library name is **liba.a**, you should get the linking adding the flag **-static -la**.

EDITED

---

### Post by supirman on 2008-07-07
pass the option -Wl,-Bstatic to g++, 

[PHP]g++ [your other stuff] -Wl,-Bstatic -la[/PHP]

---

### Post by Cygnus on 2008-07-08
Thanks for the replies. I had earlier tried with the -static flag but it only gave me errors. I now continued to investigate that and I found that this combination worked:

```
-static-libgcc -Wl,-static -la
```

-static must be passed to the linker as supirman suggested with -Wl but I also needed -static-libgcc or I ran into the error described at this link: [<debian-gcc>]("http://www.mail-archive.com/debian-gcc@lists.debian.org/msg25676.html").

---

### Post by nvteighen on 2008-07-08
But, wait: Won't -static static-link all libraries? If you want to static-link only some libraries, probably using the whole path to the .a file is the best solution (remember: A .a file is just a bunch of .o files, so both are linked the same way).

---

### Post by Cygnus on 2008-07-08
> **nvteighen said:**
> But, wait: Won't -static static-link all libraries? If you want to static-link only some libraries, probably using the whole path to the .a file is the best solution (remember: A .a file is just a bunch of .o files, so both are linked the same way).

Note that -Wl,-static goes to the linker. It only affects libraries after it. From man ld:

> You may use this option multiple times on the command line: it affects library searching for -l options which follow it. 

---

### Post by drunken_sapo on 2008-07-31
isn't there any elegant way to say to the compiler: "prefer static libraries"? If you are linking against dozens of libraries or you don't know (nor want to find out) which ones are static or shared, using the order to specify it really is not an option.
No one knows any workaround for this?

---

### Post by dribeas on 2008-07-31
> **Cygnus said:**
> Hi. I have a minor problem. Do you know how to make g++ -l flags use the .a library instead of the .so ones when both are available ? Hardcoding the path works fine, but I assume there is a better way.

In short; if you have liba.so and liba.a and specify -la to g++ it seems to pick up liba.so. Can you make it prefer .a instead ?

Your question has already been answered, just a hint: be careful with static library linking, as they are dependent on the order in which you type the link/compiler command line. An static library can depend only on symbols defined previously in the command line.

   David

---

### Post by DraconPern on 2008-08-07
Just adding a data point with g++ 4.2.3.

What you want is to minimize dependencies.  Using the -static flag doesn't do the right thing under Linux.  The only way is to specify the path of the .a file.  Specifying -L and -l does not work even if you only have .a files, g++ will not link them in.

Working example, I am linking a program that uses boost:

g++ -I ../../boost_1_35_0 reader.cpp ../../boost_1_35_0/stage/lib/libboost_system-gcc42-mt-d.a ../../boost_1_35_0/stage/lib/libboost_regex-gcc42-mt-d.a -lpthread

---

### Post by dwhitney67 on 2008-08-07
> **DraconPern said:**
> Just adding a data point with g++ 4.2.3.

What you want is to minimize dependencies.  Using the -static flag doesn't do the right thing under Linux.  The only way is to specify the path of the .a file.  Specifying -L and -l does not work even if you only have .a files, g++ will not link them in.

Working example, I am linking a program that uses boost:

g++ -I ../../boost_1_35_0 reader.cpp ../../boost_1_35_0/stage/lib/libboost_system-gcc42-mt-d.a ../../boost_1_35_0/stage/lib/libboost_regex-gcc42-mt-d.a -lpthread

Um, I think you are wrong wrt to your conclusion.  A .a library file usually consists of a collection of object files, or more appropriately stated, an archive of object files.  If the library is indeed needed by the application, then it will include it within the linked executable.

Your usage in the 'g++' statement also seems a wee bit strange.  Probably should be something like:
```
g++ -I../../boost_1_35_0 reader.cpp -L../../boost_1_35_0/stage/lib -lboost_system-gcc42-mt-d -lboost-regex-gcc42-mt-d -lpthread
```

P.S.  I'm curious... why are you using the pthread library when boost already provides wrapper constructs for threads, mutexes, etc?

---

