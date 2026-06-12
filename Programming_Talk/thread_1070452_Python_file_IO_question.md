---
title: "Python file I/O question"
date: 2009-02-15
forum: Programming Talk
---

### Post by supercheetah on 2009-02-15
I'm trying to learn Python, but I am running into a "writer's block" of sorts, or maybe I've been too corrupted by C++, or maybe I just don't know Python well enough.  I'm not sure which.

Anyway, I have a question about a file that I have open in read/write mode so that I can replace certain values in it:
```

targetfile = open(targetname, "r+")

```

Some of the values in the file that I'm trying to replace are longer than the values I'm trying to replace them with.  In other words, let's say I'm trying to replace "foobar\n" with just "foo\n" in the *targetfile*.  I can't figure out for the life of me what I need to do to get rid of the extra three characters.  I tried using '\b', but that just gave me garbage that would show up as "foo^H^H^H".

Argh!  What am I missing? :confused:

---

### Post by ssam on 2009-02-15
i dont think there is any way to do it without moving each byte after the change.

if it is something your program needs to do repeatedly then maybe you will need to find a way of holding the data in ram that makes insertion and deleting computationally cheep. (have a read of [http://en.wikipedia.org/wiki/Linked_list](http://en.wikipedia.org/wiki/Linked_list) if you are not familiar with this sort of stuff).

a list in python is internally stored as an array. there are quite a few references to python linked lists online, see [http://greenteapress.com/thinkpython/html/chap17.html](http://greenteapress.com/thinkpython/html/chap17.html) (though maybe a list will be fast enough for you. no need to optimise some thing if its fast enough already)

---

### Post by Jacks0n on 2009-02-15
You should be able to just read the file in as a string and replace all instances.

eg...

```

targetfile = open(targetname, "r+")

targetfile_new = targetfile.read().replace("foobar\n", "foo\n")

targetfile.close()

targetfile = open(targetname, "w")

targetfile.write(targetfile_new)

targetfile.close()

```

---

### Post by supercheetah on 2009-02-15
This all has to do with disk operations.

Anyway, someone on the Python IRC helped me realize that the proper way to do it to prevent data corruption is to write it to a new file, and move that one back on to the old file.

---

