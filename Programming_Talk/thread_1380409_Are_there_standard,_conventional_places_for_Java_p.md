---
title: "Are there standard, conventional places for Java programmers to put their code?"
date: 2010-01-13
forum: Programming Talk
---

### Post by lkrubner on 2010-01-13
I'm curious if there are conventions about directory use on Ubuntu, regarding Java programming? Is there a standard directory that most Java programmers use for the code they write? Are there any standard CLASSPATH locations?

---

### Post by myrtle1908 on 2010-01-13
> **lkrubner said:**
> I'm curious if there are conventions about directory use on Ubuntu, regarding Java programming? Is there a standard directory that most Java programmers use for the code they write? Are there any standard CLASSPATH locations?

I tend to do the following:-

```
/myapp
  /src
    *.java
  /lib
    third party JARs here
  /bin
    *.class here
```

This way everything is localised to the project directory which makes compiling and running simple.

Better still, use Eclipse and let it take care of it all for you ... it will build a structure similar to the above.

---

### Post by lkrubner on 2010-01-13
> **myrtle1908 said:**
> I tend to do the following:-

```
/myapp
  /src
    *.java
  /lib
    third party JARs here
  /bin
    *.class here
```


Thanks much. Do you put the /myapp directory in your home directory (your login home) or do you put it elsewhere?

---

### Post by Bruce H on 2010-01-13
Eclipse uses a 'workspace' concept, and will set up your project folder, by default, as:

/home/<user>/workspace

other directories such as lib and src may be created under that.

disclaimer: I am not a java programmer. I work mostly in PHP and Perl, and although I do use Eclipse for that, your results may vary.

---

### Post by myrtle1908 on 2010-01-13
> **lkrubner said:**
> Thanks much. Do you put the /myapp directory in your home directory (your login home) or do you put it elsewhere?

Wherever you like.  Home dir is fine eg.

~/projects/java/myapp

---

