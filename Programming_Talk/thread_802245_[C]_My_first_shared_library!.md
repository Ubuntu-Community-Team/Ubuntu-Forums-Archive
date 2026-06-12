---
title: "[C] My first shared library!"
date: 2008-05-21
forum: Programming Talk
---

### Post by nvteighen on 2008-05-21
I've been with this for a while and it (somehow) works! It's a float-precision library originally meant for [Programming Challenge 10]("http://ubuntuforums.org/showthread.php?t=783653"), but that I couldn't finish on time. Anyway, it has been really fun to do this (and I feel I've finished some good work, after all!)

I include a tar file with the source. It includes the library's source, the header file and a little test program which performs the four basic operations (+, -, *, /) with two variables. EDIT:No negatives value supported... yet.

Of course, you won't be able to use this library for anything useful ;) I'd really appreciate any comment to improve it!

To compile the shared library:
```

./make

```

To compile the test program:
```

./make float_test

```

To execute it, you'll have to set the LD_LIBRARY_PATH env variable to the program's directory or (less recommended) copy libfloat.so to /usr/lib.

To clean:
```

./make clean

```

---

### Post by Lster on 2008-05-21
Looks cool but I can't set it up properly. I tried copying it to /usr/lib (after remaking it) but I still got the error:

> ./float_test: error while loading shared libraries: libfloat.so: cannot open shared object file: No such file or directory

I'm also not sure how to set LD_LIBRARY_PATH. Any pointers? :)

---

### Post by nvteighen on 2008-05-21
> **Lster said:**
> Looks cool but I can't set it up properly. I tried copying it to /usr/lib (after remaking it) but I still got the error:



I'm also not sure how to set LD_LIBRARY_PATH. Any pointers? :)

Do this in bash:
```

export LD_LIBRARY_PATH=./:$LD_LIBRARY_PATH

```

This will add "./" to the variable (change it to something else if you want); remember that will be forgotten after logging out, so if you want to make that change permanent, you should add that line to your .bashrc file.

While copying to /usr/lib, have you checked permissions? You should chmod it to 644 (no execution permission needed).

---

