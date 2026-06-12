---
title: "file indexer"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by vinboy on 2008-05-29
hi
I'm looking for a simple file indexer.
I've tried beagle and tracker but dislike them.

Here is my requirement:
- Only index the specified directories
- Only index the filename (DO NOT index contents)
- Either text or gui based. I'd actually prefer text-based, but either is fine.

Something like this is pretty close to what i'm looking for [http://perlfindexer.sourceforge.net/](http://perlfindexer.sourceforge.net/)

thanks for your time :guitar:

---

### Post by unutbu on 2008-05-29
> **vinboy said:**
> 
- Only index the specified directories
- Only index the filename (DO NOT index contents)
- Either text or gui based. I'd actually prefer text-based, but either is fine.

It sounds like `locate` or `find` fit the bill.

For example, to find all files on your system whose name includes the string "adobe" you can run
```

locate adobe
``` or
```
find / -name adobe
```

If you want to run an arbitrary command on each file found by either command, you can then use xargs like this:

```
locate adobe | xargs ls -l
```

You can also limit your search to certain directories. For example, if you want to list all pdfs in your home directory you could do something like

```
locate pdf | grep /home/username.*\.pdf$ | xargs ls -l
```

If there is some other functionality you want, describe it and maybe I'll know a command-line way to do it.

---

### Post by dbera on 2008-05-30
> **vinboy said:**
> hi
I'm looking for a simple file indexer.
I've tried beagle and tracker but dislike them.

Here is my requirement:
- Only index the specified directories
- Only index the filename (DO NOT index contents)
- Either text or gui based. I'd actually prefer text-based, but either is fine.

Something like this is pretty close to what i'm looking for [http://perlfindexer.sourceforge.net/](http://perlfindexer.sourceforge.net/)

thanks for your time :guitar:

[http://beagle-project.org/Static_Indexes](http://beagle-project.org/Static_Indexes)

with option "--disable-filtering" for not indexing contents.

---

### Post by vinboy on 2008-06-01
thanks guys. I'm taking a look now. Gonna take awhile to learn these stuff.

I was hoping for a more specific program that can do the job without having to read a bunch of stuff.
ok the static indexes sound like what I want.

---

