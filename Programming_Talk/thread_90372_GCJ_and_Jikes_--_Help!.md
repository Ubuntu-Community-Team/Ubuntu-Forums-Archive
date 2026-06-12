---
title: "GCJ and Jikes -- Help!"
date: 2005-11-14
forum: Programming Talk
---

### Post by Burke on 2005-11-14
I debated whether to put this in the programming forum or not, as it seems to be a dependency issue, but here goes:

When I try to compile something with GCJ, here's what I get:

/usr/lib/gcc/i486-linux-gnu/4.0.2/../../../../lib/crt1.o: In function `_start':
../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status

And here's what I get when I try the same thing w/ Jikes: 

*** Semantic Error: You need to modify your classpath, sourcepath, bootclasspath, and/or extdirs setup. Jikes could not find package "java.lang" in:
                .

I've tried everything I can think of, and nothing is working.  Can anyone help me?  I don't need both working (If it's one or the other, I'll choose GCJ), but I thought the output of both might be helpful.

Any input would be greatly appreciated.

Thanks

Burke

---

### Post by MichaelM on 2005-11-14
What JDK do you have installed?

---

### Post by Burke on 2005-11-14
uhh.... this is going to sound *really* retarded, but how do I tell?

All I know is I have semi-working installations of two compilers and a flawless installation of vim :)

---

### Post by Boris2 on 2005-12-09
I just found your posting via the search. Perhaps I can help you, if you did no find out yourself.

For gcj you have to define the Class which contains your main()
```
gcj Test.java --main=Test
```

For jikes you need to tell which classpath to use
```
jikes -bootclasspath /usr/share/classpath/glibj.zip [...]
jikes -bootclasspath /usr/lib/j2se/1.4/jre/lib/rt.jar [...]
```

---

### Post by Burke on 2005-12-09
Haha... Perfect!  Such an easy fix :)

Thanks a million.

Burke

---

