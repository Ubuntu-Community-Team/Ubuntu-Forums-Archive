---
title: "Problem while cross-compiling"
date: 2012-09-05
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-05
Hey,
I am trying to cross compile an application. When I run a make, it gives me the following error

```

Removing libraries from /home/projects/lib.
find: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian
make[1]: *** [clean] Error 127

```

Is there any work around ?

---

### Post by IAMTubby on 2012-09-05
Even if I run a simple shell command, say ls or clear in this location, from where I'm trying to run the code, it gives me the same error

```

ls: error while loading shared libraries: libc.so.6: ELF file data encoding not little-endian

```

---

### Post by muteXe on 2012-09-05
[http://gcc.gnu.org/bugzilla/show_bug.cgi?id=41818](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=41818)

any use?

---

### Post by IAMTubby on 2012-09-05
> **muteXe said:**
> [http://gcc.gnu.org/bugzilla/show_bug.cgi?id=41818](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=41818)

any use?
1)Will go through it and get back to you. 
I know LD_LIBRARY_PATH is an environment variable. What is it used for ?

2)What is the purpose of environment variables, when everytime you open a new terminal the value is lost ?

3)Is shell variable and env variable the same thing ?

---

### Post by muteXe on 2012-09-05
[http://stackoverflow.com/questions/7148036/what-is-ld-library-path-and-how-to-use-it](http://stackoverflow.com/questions/7148036/what-is-ld-library-path-and-how-to-use-it)

[http://en.wikipedia.org/wiki/Environment_variable#Persistence](http://en.wikipedia.org/wiki/Environment_variable#Persistence)

[http://docstore.mik.ua/orelly/unix/upt/ch06_01.htm](http://docstore.mik.ua/orelly/unix/upt/ch06_01.htm)


Seriously, google is your friend.

---

### Post by IAMTubby on 2012-09-05
I got to build, but not completely by adding the line
export LD_LIBRARY_PATH=/home/local/lib:/lib:/usr/lib:

But it fails after some time. Okay, some improvement from the previous tries, but it still fails. Do I have to add something like this.
```

--build = build 
--host = host
--target = target

```
But I'm not sure on what to give here.

Please advise.
Thanks.

---

