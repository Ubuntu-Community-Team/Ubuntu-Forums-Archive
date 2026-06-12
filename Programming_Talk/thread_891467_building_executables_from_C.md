---
title: "building executables from C"
date: 2008-08-16
forum: Programming Talk
---

### Post by Windy Peaks on 2008-08-16
Ladies and Gentlemen of the forum:

Does anyone know which command or ubuntu program can create a executable program from a compiled C program ??

Thanks in Advance
Windy

---

### Post by iaculallad on 2008-08-16
> **Windy Peaks said:**
> Ladies and Gentlemen of the forum:

Does anyone know which command or ubuntu program can create a executable program from a compiled C program ??

Thanks in Advance
Windy

I remembered reading your post a while ago and was moved by a forum administrator  to the [Programming]("http://ubuntuforums.org/showthread.php?t=891410") category. Stick with that post as you will get more responses when in that category.

---

### Post by Cypher on 2008-08-16
```

sudo apt-get install build-essential

```
This will get you the compilers.

At the most basic, you can compile a C program with
```

gcc -o app app.c

```

But without actual details of the program, that's all I can give you..

---

### Post by jrothwell97 on 2008-08-16
It depends. Normally if the files are already compiled, you'd use ```
ld
```, but the linker functionality is built into GCC these days so it should be fairly automatic.

First, run

```
$ sudo apt-get install build-essential
```

to grab the compilers and the header files.

If you're using a one-file program, it'll be a simple "gcc infile.c -o outfile". For example, if I wanted to compile and build *goodbye.c* and call the executable *goodbye*, I would run

```
$ gcc goodbye.c -o goodbye
```

Then, to set permissions:

```
$ chmod +x goodbye
```

And finally, to *run* the program:

```
$ ./goodbye
Goodbye, cruel world.
$
```

If you're building a program with a file called Makefile in its folder, it's even easier: change into that directory, and then run

```
./configure
sudo make
sudo make install
```

the README file should tell you where the app will have been installed, and you should be able to change it with a command-line switch.

---

### Post by overdrank on 2008-08-16
Moved :)

---

### Post by dwhitney67 on 2008-08-16
> **jrothwell97 said:**
> It depends. Normally if the files are already compiled, you'd use ```
ld
```, but the linker functionality is built into GCC these days so it should be fairly automatic.

First, run

```
$ sudo apt-get install build-essential
```

to grab the compilers and the header files.

If you're using a one-file program, it'll be a simple "gcc infile.c -o outfile". For example, if I wanted to compile and build *goodbye.c* and call the executable *goodbye*, I would run

```
$ gcc goodbye.c -o goodbye
```

Then, to set permissions:

```
$ chmod +x goodbye
```

And finally, to *run* the program:

```
$ ./goodbye
Goodbye, cruel world.
$
```

If you're building a program with a file called Makefile in its folder, it's even easier: change into that directory, and then run

```
./configure
sudo make
sudo make install
```

the README file should tell you where the app will have been installed, and you should be able to change it with a command-line switch.
Some of your advice is correct, but other parts are not necessarily correct.

- I would never recommend using 'ld' directly; use gcc.

- There is no need to perform the 'chmod'; gcc will automatically set the executable to the proper permissions.

- Not all projects have a 'configure' script.

- One does not necessarily need to use 'sudo' when running 'make' (with or without the install directive).  Some projects are written/compiled for the user only and do not need to be installed in root-owned directories.

---

### Post by jinksys on 2008-08-16
> **dwhitney67 said:**
> 
- One does not necessarily need to use 'sudo' when running 'make' (with or without the install directive).  Some projects are written/compiled for the user only and do not need to be installed in root-owned directories.

Another reason why reading the README if always good :)

---

### Post by dwhitney67 on 2008-08-16
> **jinksys said:**
> Another reason why reading the README if always good :)
I write C/C++ applications and associated Makefiles all of the time (for personal usage), and I do not have a README file.  Am I doing something wrong?

I was implying earlier that when building, whether using gcc/g++ or a Makefile, there is no need to run sudo, unless the user is installing something into a directory in which he/she lacks write permissions.

---

### Post by jinksys on 2008-08-16
> **dwhitney67 said:**
> 
I was implying earlier that when building, whether using gcc/g++ or a Makefile, there is no need to run sudo, unless the user is installing something into a directory in which he/she lacks write permissions.

When compiling source packages that use automake (ie: those who have a ./configure file) it is assumed by the software that it will be installed to /usr/local

```

$ ./configure --help

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

```

If you do not specify an alternate prefix, you will need root access to install the software.  However, if the developer did not use automake and handcoded their Makefile, then I would strongly recommended reading the README as it may have valuable info.  That is, if the developer took the time to write a decent README.

> 
I write C/C++ applications and associated Makefiles all of the time (for personal usage), and I do not have a README file.  Am I doing something wrong?


README files are generally not for the developer, they are for end users.  If you are writing software for yourself, then you know exactly what your program does so a README file would be pointless.

---

