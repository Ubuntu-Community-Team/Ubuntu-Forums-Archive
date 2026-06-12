---
title: "compile specific source file in Linux coreutils package"
date: 2014-10-25
forum: Packaging and Compiling Programs
---

### Post by mahmoud7 on 2014-10-25
I need to compile a specific version of cp (copy)  command from the Linux coreutils source file. Instead of compiling the whole  package.
iam  just add a printf statement at the end of the function.
I am using Ubuntu 14.04, the source code of cp command is exist in the following directory.

**/tmp/coreutils/coreutils-8.21/src/cp.c**

how to compile it, so when run the cp command i can see the statement that i had added it in the code?
please help me?!

---

### Post by thibaud-ecarot on 2014-10-26
Hello,

You want replace command "cp" in your Ubuntu system ? it's correct ?

List of all bash command are here :
```
$ whereis cp
cp: /bin/cp /usr/share/man/man1/cp.1.gz

```

You can add your new "cp" program in this folder /bin/ but it's dangerous. /!\

For compiling your source code of coreutils you must :
```

$ cd coreutils        
$ ./configure --quiet #[--enable-gcc-warnings] 
[*]       
$ make        
$ make check
```

try it.

Have a nice day.

---

### Post by /ADM on 2014-10-26
First, never place your compiled binaries into /bin.  EVER.  Always put them in /usr/local/bin.  However when using cp, the system would choose the one in /usr/bin first, so you could rename it to mycp or something.

Second, would it not be easier compiling your own program for just a printf statement test?  Like a hello world?

---

