---
title: "GCC &amp; GMP: Can't compile simple program"
date: 2005-12-31
forum: Packaging and Compiling Programs
---

### Post by veraction on 2005-12-31
Newbie problem solved.

Forgot to use the -lgmp option on gcc](*,)

[edit] Can compile fine now, just can't figure out how to run it:

```
$ ./a.out
./a.out: error while loading shared libraries: libgmp.so.3: cannot open shared object file: No such file or directory
```

OK, another newbie problem **solved**: It wasn't finding the shared libraries. When I compiled gmp, it placed the libraries in /usr/local/lib. I fixed the problem by making links to these libraries and placing them in /lib

```

$ cd /lib
$ sudo ln -s /usr/local/lib/libgmp.so
$ sudo ln -s /usr/local/lib/libgmp.so.3

```

Now it seems to work.. for now :)

---

### Post by ape on 2005-12-31
the other thing you can do in this situation would be to set your LD_LIBRARY_PATH variable to include the /usr/local/lib directory.  Depends on if you start having too many symlinks to manage..<G>

---

### Post by veraction on 2005-12-31
BTW, how would I go about doing that?

I know I can use *env* to show variable things, and also *echo $PATH* to display paths, but I don't know how to set them. I tried using *set* but am not sure on how it is used (no man page). I tried adding one, but it didn't show up in the *env* output. Also checked [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) for info, didn't find anything (not sure what to search for, cause my terms don't work)

---

### Post by ape on 2006-01-01
veracation,

   The way to set variables depends on your shell derivative:

        If you are using an sh derivative (bash, zsh, etc...) you would issue the following command:


         export LD_LIBRARY_PATH=/usr/local/lib:${LD_LIBRARY_PATH}

        If you are using a csh derivative (csh, tcsh) you would issue the following command:

         setenv LD_LIBRARY_PATH /usr/local/lib:${LD_LIBRARY_PATH}

After running either one of these commands, you should be able to issue `echo $LD_LIBRARY_PATH` and see what you have set.

---

### Post by veraction on 2006-01-01
ah, thanks.  I'm using bash. I had tried setenv, but now I understand

---

