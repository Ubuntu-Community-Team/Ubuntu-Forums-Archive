---
title: "source code for /lib/ld-linux.so.2"
date: 2013-02-23
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-23
Hello,
I would like to know what kind of processing takes place when linux's dynamic linker/loader finds and loads a shared library. I understand it is /lib/ld.so or /lib/ld-linux.so.2 that does it.
Where do I find the source code for the same ?

I tried downloading the glibc source code, but couldn't find anything there. 
I am now trying out [http://koala.cs.pub.ro/lxr/glibc/](http://koala.cs.pub.ro/lxr/glibc/) but don't know where exactly it is found.

Thanks.

PS : From the man page for ld.so, I could get a list of steps(like DT_RPATh followed by LD_LIBRARY_PATH followed by DT_RUNPATH followed by, /etc/ld.so.cache, /lib, /usr/lib, but I would like to have a look at the code and appreciate)

---

### Post by spjackson on 2013-02-23
apt-file find tells me that this is part of the libc6 package. The source for that is [here.]("http://packages.ubuntu.com/source/quantal/eglibc")

---

### Post by IAMTubby on 2013-02-23
> **spjackson said:**
> apt-file find tells me that this is part of the libc6 package. The source for that is [here.]("http://packages.ubuntu.com/source/quantal/eglibc")
spjackson, I went to this page , [http://packages.ubuntu.com/quantal/libc6](http://packages.ubuntu.com/quantal/libc6) and I get a lot of packages. Would it be possible to tell me where exactly I can find the ld.so source ? Just a bit confused.

---

### Post by spjackson on 2013-02-23
> **IAMTubby said:**
> spjackson, I went to this page , [http://packages.ubuntu.com/quantal/libc6](http://packages.ubuntu.com/quantal/libc6) and I get a lot of packages. Would it be possible to tell me where exactly I can find the ld.so source ? Just a bit confused.
At the top of the page you mention, there's a bit that says: "[Source: eglibc]". If you click on the eglibc link, then you get taken to the page that I already referred you to, i.e. this one: [http://packages.ubuntu.com/quantal/libc6]("http://packages.ubuntu.com/quantal/libc6")

This thing called "source" is the source from which the binary packages are built. If you scroll down to the bottom, there's a heading that says "Download eglibc", and below that you will find 3 downloads. eglibc_2.15.orig.tar.gz is the original upstream source. The other two are to do with patching and building for Ubuntu.

I hope you can manage to download that, unpack it and figure out which is the source you want.

---

### Post by IAMTubby on 2013-02-23
> **spjackson said:**
> 
I hope you can manage to download that, unpack it and figure out which is the source you want.
spjackson, thanks a lot :)
I went through the source ...\glibc\eglibc-2.15\elf\ldconfig.c and wow, I was actually able to understand a few things.

Thanks a lot once again.

---

### Post by IAMTubby on 2013-02-23
spjackson,
May I ask one more question,
Based on reading webpages and seeing a little bit of the code, my understanding of ldconfig is that it does 2 things. 
**1.** create sym link from soname to realname
**2.** make a list of all the so's under the various dir's in /etc/ld.so.conf and write it in a cache called /etc/ld.so.cache with the path(I saw the output using **ldconfig -p**)
Am I right here ?

But I made an so and copied it in /usr/lib/i386-linux-gnu and ran the exe without doing ldconfig, and it still worked. How's that? the cache hasn't got updated and so doesn't know where to find my so right ?**( $ldconfig -p | grep foo doesn't show anything, but the exe still runs, I'm a bit confused here)**

---

### Post by trent.josephsen on 2013-02-23
Have you read [this one](http://www.acsu.buffalo.edu/~charngda/elf.html)? Quite good content despite the terrible page design.

---

### Post by IAMTubby on 2013-02-26
> **trent.josephsen said:**
> Have you read [this one](http://www.acsu.buffalo.edu/~charngda/elf.html)? Quite good content despite the terrible page design.
trent.josephsen, over the last 2 days, I have put in a lot of effort trying to understand so's. I have understood most of the things. I have a few questions, however.

1. Is it possible to append to /etc/ld.so.cache from **"any random dir/user specified dir"** by doing ldconfig? I tried doing ldconfig -n . , but that doesn't seem to work.

2. Which are the directories on which ldconfig operates ? Are they, **a)everything mentioned in /etc/ld.so.conf.d/*.conf** + **b)/lib** + **c)/usr/lib ?**

3. Don't you think all paths in the makefile should also be added to the list of dir's an "so" is searched in ? That would take away the overhead of adding paths where so's exist to LD_LIBRARY_PATH since these are already mentioned at build time. Why mention them again at runtime ? EDIT:*probably, /etc/ld.so.conf should have a file like fromMakefile.conf* :)

4. I copied an "so" to /usr/lib/i386-linux-gnu and was able to run the file, WITHOUT doing an ldconfig. Is that because
**a)** since it is under /usr/lib, it will run even if it doesn't figure in /etc/ld.so.cache OR
**b)** all directories under /etc/ld.so.conf.d/*.conf are manually searched for so's if it is not found in the cache?

5. I find the output of ldconfig lacking information about which "realname" it is currently running. I understand it will be something like libname.so.MAJOR.LATESTMINOR, but ldconfig doesn't tell me which one is the latest.

6. I don't understand why ldconfig should hold information of this nature.
libname.so.1 ==> /usr/lib/i386-linux-gnu/libname.so.1
According to me libname.so ==> /usr/lib/i386-linux-gnu/libname.so is sufficient.
I mean, the user would only enter something like -lname. so as long as information about libname.so is maintained, all others can be found through soft links.

EDIT : adding 3 more questions

7.Why do we mention the major number part also in the realname ? I mean it's confusing someone could make an so like, $gcc -shared -Wl,-soname,libname.so.33 -o libname.so.1.14 lib.o. I mean in the actual SONAME field, the soname would be libname.so.33, but someone looking at the libname.so.1.14 alone would think it is libname.so.1.

8.Don't you think finding the latest minor number which belongs to a particular major number should be done based on **timestamp** and **not by text parsing the realname** and finding out the number after the dot ?

9.**Don't you think a file like libname.so.1(soname file) should NOT exist on disk.**. Please check the attached picture. It is self explanatory as to how **ldconfig creates a file named libname.so.1 (to help in it's processing ?) even if I have only 2 so's libname.so and libname.so.1.0**. The fact that libname.so.1->libname.so.1.0 tells me what the purpose of the file is, and this will keep on getting updated as and when a new (minor number) version of the library is added. But surely, ldconfig doesn't need to show this file on disk, does it?

Please advise.
Thanks.

---

### Post by trent.josephsen on 2013-02-26
I wish I could help you. Unfortunately, the site I last linked pretty much exhausts my knowledge of Linux loading mechanics; I tend to work on a considerably lower level. Good questions, though, I hope you find the answers.

---

### Post by IAMTubby on 2013-02-27
> **spjackson said:**
> 
I hope you can manage to download that, unpack it and figure out which is the source you want.
> **trent.josephsen said:**
> Good questions, though, I hope you find the answers.
thanks trent.josephsen, spjackson. 
I understand so's much better now, but (for the purpose of better understanding alone), I would like to question a few things as to why they are done in a particular way, and whether it really is necessary/why it couldn't be done differently (**POINTS 3,5,6,7,8,9 above especially)**. 

It would be great if you could answer even a couple of questions. That would give me more pointers to google and find the remaining answers.

Thanks :)

---

