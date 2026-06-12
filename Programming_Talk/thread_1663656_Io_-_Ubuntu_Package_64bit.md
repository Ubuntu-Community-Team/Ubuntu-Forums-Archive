---
title: "Io - Ubuntu Package? 64bit?"
date: 2011-01-09
forum: Programming Talk
---

### Post by cprofitt on 2011-01-09
Hello:

I have done a Google search and not found a package for Ubuntu and installing from the Io home page ([http://iolanguage.com/](http://iolanguage.com/)) and following the install instructions failed.

I am curious if anyone here has programmed in Io on Ubuntu... if you have is there a package? will it work on 64bit?

Thanks,

---

### Post by Bucky Ball on 2011-01-09
From the link:

> **platforms**

       OSX, **Linux**, BSD, Windows 
Should work on Ubuntu, can't help with the rest. ;)

---

### Post by cprofitt on 2011-01-11
> **Bucky Ball said:**
> From the link:

Should work on Ubuntu, can't help with the rest. ;)

It should, but it failed on me. That is why I was asking for a package or advice from someone on getting it installed.

---

### Post by Simian Man on 2011-01-11
I just installed it successfully on Fedora 14, so it should be easily doable on Ubuntu.  What steps did you take and what error did you get?

---

### Post by cprofitt on 2011-01-11
> **Simian Man said:**
> I just installed it successfully on Fedora 14, so it should be easily doable on Ubuntu.  What steps did you take and what error did you get?

Was it 64bit or 32bit...

I think the issue may have been missing libraries that are 32bit.

I will endeavor to try the install again and post the errors tonight.

---

### Post by Simian Man on 2011-01-11
> **cprofitt said:**
> Was it 64bit or 32bit...

I think the issue may have been missing libraries that are 32bit.

I will endeavor to try the install again and post the errors tonight.

64 bit, but it seems like that shouldn't matter if you build it from source.

---

### Post by josephellengar on 2011-03-14
bump. Any conclusion? Same problem.

---

### Post by Simian Man on 2011-03-15
What is the actual problem you are having?  Like I said, it installed for me with no trouble at all, though I removed it a while ago.

---

### Post by josephellengar on 2011-03-15
> **Simian Man said:**
> What is the actual problem you are having?  Like I said, it installed for me with no trouble at all, though I removed it a while ago.

I'm trying to install it from source using the directions from the download package at [http://iolanguage.com/](http://iolanguage.com/).

The directions I used are:

```

nsure you are at the top level of the source tree, that is where this file lives. From here, you are in the right spot to enter these commands:

mkdir build && cd build
cmake ..
make install

If you do not wish to install, just run "make" instead of "make install". Currently there is no analogue to the old "make linkInstall". However, if you have used linkInstall in previous versions of Io, you should never have to run linkInstall again, since it created symbolic links to where your Io source was at that time. The only time you would have to do this again, is if you moved the Io source from one dir to another. Most people don't.

```



This is what I got (at the end). No compiler errors. However, it won't work or run the script.

```

-- Installing: /usr/local/lib/io/addons/Zlib/_build/binaries
ross@ross-laptop:~/Desktop/stevedekorte-io-4907d9d/build$ ls
CMakeCache.txt  Makefile  addons               install_manifest.txt  tools
CMakeFiles      _build    cmake_install.cmake  libs
ross@ross-laptop:~/Desktop/stevedekorte-io-4907d9d/build$ cd ..
ross@ross-laptop:~/Desktop/stevedekorte-io-4907d9d$ ls
CMakeLists.txt  _build  build     docs    libs     modules  scm      tools
README.txt      addons  build.sh  extras  license  samples  test.io
ross@ross-laptop:~/Desktop/stevedekorte-io-4907d9d$ io test.io 
io: error while loading shared libraries: libbasekit.so: cannot open shared object file: No such file or directory
ross@ross-laptop:~/Desktop/stevedekorte-io-4907d9d$ io
io: error while loading shared libraries: libbasekit.so: cannot open shared object file: No such file or directory
ross@ross-laptop:~/Desktop/stevedekorte-io-4907d9d$ 

```

---

### Post by MadCow108 on 2011-03-15
I have not tried it but probably make install will install it in /usr/local
the library folder of that prefix is not searched by ld.so, the dynamic linker.
either add it to the environment variable LD_LIBRARY_PATH or place it in the /etc/ld.so.conf (or less recommended configure with -DINSTALL_PREFIX=/usr)

have you filed a request for packaging in debian or ubuntu? maybe someone will provide a package on request.

---

### Post by Simian Man on 2011-03-15
> **MadCow108 said:**
> I have not tried it but probably make install will install it in /usr/local
the library folder of that prefix is not searched by ld.so, the dynamic linker.
either add it to the environment variable LD_LIBRARY_PATH or place it in the /etc/ld.so.conf (or less recommended configure with -DINSTALL_PREFIX=/usr)

Yes that is almost certainly the problem.  It tells you in the [README]("https://github.com/stevedekorte/io/blob/master/README.txt") (line 34) that you need to run ldconfig with /usr/local/lib in your path.

---

### Post by josephellengar on 2011-03-15
> **MadCow108 said:**
> I have not tried it but probably make install will install it in /usr/local
the library folder of that prefix is not searched by ld.so, the dynamic linker.
either add it to the environment variable LD_LIBRARY_PATH or place it in the /etc/ld.so.conf (or less recommended configure with -DINSTALL_PREFIX=/usr)

have you filed a request for packaging in debian or ubuntu? maybe someone will provide a package on request.

That worked. Thank you. I'll file a package request.

---

