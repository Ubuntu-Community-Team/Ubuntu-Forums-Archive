---
title: "Java: add java.xml lib to Eclipse?"
date: 2009-01-11
forum: Programming Talk
---

### Post by andrew222 on 2009-01-11
Hello,

I was just trying to run a program from the Cay Hortsmann book 'Big Java' which is an XML parser.  I was getting an error message telling me that importing from java.xml.*; can not be resolved.  Is there a way I can add this library so i can use it with any IDE and with command line compilations?

Also, I need to do an 'import org.*; as well, any help is welcome!

Rgds,

Andrew

---

### Post by kavon89 on 2009-01-11
Check if there is a CD that came with the book, containing examples and more importantly the libraries.

Also, execute " java -version " in your operating system's command line. Java 6 should come with xml libraries.

```
import javax.xml.*;
```

---

### Post by andrew222 on 2009-01-11
Yes, after double checking the code it should be 'javax.xml.*'.  I got too ahead of myself, i'll check you a thanks and call this thread as solved...

---

### Post by drubin on 2009-01-13
> **andrew222 said:**
> Yes, after double checking the code it should be 'javax.xml.*'.  I got too ahead of myself, i'll check you a thanks and call this thread as solved...

In general if your thread is solved you should use the thread tools right above your first post of the thread. see [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Glad things worked out in the end.

EDIT:
Thanks solved feature was still enabled when I posted this. (not sure if it will be back or not) see [this]("http://ubuntuforums.org/showpost.php?p=6544653&postcount=9")

---

### Post by jespdj on 2009-01-14
> **andrew222 said:**
> and call this thread as solved...
You can set your own thread to "SOLVED" using the Thread Tools menu in the top right of the page.

*edit*: too late... :)

---

### Post by drubin on 2009-01-14
> **jespdj said:**
> You can set your own thread to "SOLVED" using the Thread Tools menu in the top right of the page.

*edit*: too late... :)

hehehe :)

---

