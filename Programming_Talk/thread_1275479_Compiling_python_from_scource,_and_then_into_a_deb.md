---
title: "Compiling python from scource, and then into a deb"
date: 2009-09-25
forum: Programming Talk
---

### Post by The-ITu on 2009-09-25
hi,
I just created this awesome python application and i want to spread it around, but every one has python.
I was just wondering if I could compile python source into a linux executable like py2exe, and then compile the executable into a .deb installer file.

any help would be appreciated.
thanks, The-ITu

---

### Post by -grubby on 2009-09-26
> **The-ITu said:**
> hi,
I just created this awesome python application and i want to spread it around, but every one has python.

I was just wondering if I could compile python source into a linux executable like py2exe, and then compile the executable into a .deb installer file.

I googled around a little for guides on making .debs, you may want to check out [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/).

As for compiling Python, well, you don't. On linux, you just make your package depend on Python.

---

### Post by The-ITu on 2009-09-28
ok thanks.....

---

### Post by dinxter on 2009-09-28
theres also tutorials, logs from past years developer weeks and all sorts of how to package stuff
[https://wiki.ubuntu.com/Packaging/Training](https://wiki.ubuntu.com/Packaging/Training)
the resources section has a number of good tutorials

---

### Post by lexen on 2009-12-20
Hello, I am trying to do this as well.  I know that you can run python from source, as I do often, but I would still like to compile it into an ubuntu package for distribution purposes.  I did not find anything at the link that specificly explained how to compile a python package, though there is a good chance I missed it.  Is there any link that goes through the specific steps?


Thanks,
Lexen

---

### Post by SevenMachines on 2009-12-20
you might want to look over the [python packaging guide]("https://wiki.ubuntu.com/PackagingGuide/Python") for some pointers

---

### Post by lexen on 2009-12-20
Thank you!  That was very helpful.  I read through it all, and while I didn't get the example to work, I think it is setting me on the right track.

Thanks!

---

