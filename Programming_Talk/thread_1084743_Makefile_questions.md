---
title: "Makefile questions"
date: 2009-03-02
forum: Programming Talk
---

### Post by svk on 2009-03-02
I'm a little bit confused about makefiles.  According to the [documentation]("http://www.cs.utah.edu/dept/old/texinfo/make/make.html#SEC5"), a rule has the following format:

```
 target ... : dependencies ...
     command
        ...
        ...
```

I was told that the command part can be any shell command.  With that in mind, I tried to do this in my makefile:

```

final: 
     ls *.o 
     tar  cf  final.tar  makefile  *.cpp   *.h
```

I was expecting that the ls commands would simply print out all the filenames that have  the .o extension.  Instead, I got this:

serg@bijou:~/Desktop$ make final
ls *.o
ls: cannot access *.o: No such file or directory
make: *** [turnin] Error 2

And it never creates the tar archive on the next line of the makefile.  Why doesn't this work and how can I fix it?

---

### Post by simeon87 on 2009-03-02
That's indeed what ls *.o does but it appears there are no *.o files in the directory:

```

ls *.o
ls: cannot access *.o: No such file or directory

```

ls does run but it can't find any .o files.

---

### Post by svk on 2009-03-02
Can I prevent make from failing if ls doesn't find any .o files?

---

### Post by tneva82 on 2009-03-02
> **svk said:**
> Can I prevent make from failing if ls doesn't find any .o files?

Not sure how elegant solution this is but before ls command touch some sort of obj file you are SURE nobody creates(like touch gerherrhergwefhrthht.o. That ought to be something nobody in their mind creates themselves ;-). later you could remove that file as well.

Just a thought. Used something similar on windows command file once.

Of course bad side is that said .o file would then be visible in the listing :-/

---

### Post by dwhitney67 on 2009-03-02
> **svk said:**
> Can I prevent make from failing if ls doesn't find any .o files?

Yes, if you precede the command you are attempting to run with a dash-character ('-').  For example:
```

final: 
     -ls *.o 
     tar  cf  final.tar  makefile  *.cpp   *.h

```

P.S.  If you are on Windoze, the -k option instructs the build process to continue.

---

