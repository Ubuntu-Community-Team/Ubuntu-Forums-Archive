---
title: "[SOLVED] Installed Boost from source, but isn't found by linker"
date: 2008-06-15
forum: Packaging and Compiling Programs
---

### Post by Nameless_one on 2008-06-15
I am trying to use the latest boost library. 

I downloaded it, and followed the instructions to install it:

> 5.1   Easy Build and Install

Issue the following commands in the shell (don't type $; that represents the shell's prompt):

$ cd path/to/boost_1_35_0
$ ./configure --help

Select your configuration options and invoke ./configure again without the --help option. [...] Also, consider using the --show-libraries and --with-libraries= options to limit the long wait you'll experience if you build everything. Finally,

$ make install

will leave Boost binaries in the lib/ subdirectory of your installation prefix. You will also find a copy of the Boost headers in the include/ subdirectory of the installation prefix, so you can henceforth use that directory as an #include path in place of the Boost root directory.

After that, I try to include it in a C++ test file, but the compiler says 

```
test.cpp:8: error: &#8216;boost&#8217; has not been declared
```

I have checked the directory, boost is there. I also ran the compiler with the option -I/usr/local/include/boost-1_35/. Nevertheless, boost is not recognized. What am I doing wrong?

---

### Post by Nameless_one on 2008-06-16
Bumpity bump.

---

### Post by WW on 2008-06-16
Show your test program, and the exact commands that you use to compile and link it.

---

### Post by Nameless_one on 2008-06-17
Hm. Now this is strange. After I rebooted, my test program works. However, the program I installed boost to actually compile, does not do so. 

I am trying to install deluge, version 0.6, and the default setup tries to compile the (included) libtorrent library, and for that it apparently needs boost. However, the installer can't seem to find boost. 

Here is the output:

[http://pastebin.com/m76527190](http://pastebin.com/m76527190)

The "Getting started" section of boost's docs say I have to include the switch "-I /usr/local/include/boost-1_35/" when I compile with boost support. 

This is the setup.py python installation script for deluge 0.6.

[http://pastebin.com/m2c5959b1](http://pastebin.com/m2c5959b1)

I am trying to put the -I switch either here: ```
_extra_compile_args = [
    "-DTORRENT_USE_OPENSSL=1",
    "-O2",
    "-D_FILE_OFFSET_BITS=64",
    "-DNDEBUG",
    ]
```

or here: ```
_include_dirs = [
    './libtorrent',
    './libtorrent/include',
    './libtorrent/include/libtorrent',
]
```

but that didn't help. Same result: 

/usr/bin/ld: cannot find -lboost_filesystem
collect2: ld returned 1 exit status
error: command 'gcc' failed with exit status 1

I know this is kind of specialized, but I hope someone can help me.

---

### Post by Nameless_one on 2008-06-19
I got this to work, although in a very peculiar manner. 

First of all, I found the directory /usr/local/lib/, which contained the .so boost files. Those were the ones I needed after all, not the source files which were contained in /usr/local/include/. These are for including in programs. 

So, I added filled this in the _library_dirs:
```
_library_dirs = [
    '/usr/local/lib'
]

```

However, I still got the errors. What happened was, setup.py was looking for a file named, for example, liboost_filesystem.so, and the existing file was named libboost_filesystem-gcc41-mt.so. I would guess these would match, but they didn't. However, when I changed the list of packages in setup.py, to boost_*-gcc41-mt, instead of just boost_*, it found them an compiled just fine. 

Is that normal behaviour? Is the linker, with the switch -llib_name, not supposed to match a file named lib_name-version.so?

---

