---
title: "[SOLVED] (defpackage :help-madness)"
date: 2008-05-31
forum: Programming Talk
---

### Post by Lau_of_DK on 2008-05-31
Gents,


I wrote a little library in Lisp, by which you can use every data type as a lazy stream, greatly inspired by the SICP videos. Anyway, it works great and I'm very happy with it. So happy in fact that I want to use it in one of my other projects - but how do I do this?

I tried prefixing my lib with

```

(defpackage ":COM.BESTINCLASS.STREAMS"
  (:use "COMMON-LISP")
  (:export :the-empty-strem
           :cons-streams
           :head
           :tail
           :empty-stream?
           :map-stream
           :filter-stream
           :append-streams
           :enum-interval
           :flat-map
           :flatten
           :accumulate
           :nth-stream))

```

And that compiles like it should. Then afterwards I load up my other project, and start off with 

```

(use-package :com.bestinclass.streams)
   or
(in-package :com.bestinclass.streams)

```

No matter what - I get a "function undefined" when I try to execute them with unqualified names. (I think it was the same with qualified names).

Somebody sharp with packages that can help me out?


/Lau

---

### Post by Lau_of_DK on 2008-05-31
Come on folks,

Somebody's gotta have a take on this? :)


/Lau

---

### Post by Jessehk on 2008-05-31
Look into ASDF for help with conditional compilation and requiring external libraries.

---

### Post by Lau_of_DK on 2008-05-31
> **Jessehk said:**
> Look into ASDF for help with conditional compilation and requiring external libraries.

This is not ASDF related.

/Lau

---

### Post by Alasdair on 2008-05-31
The problem is on the following line:
```
(defpackage ":COM.BESTINCLASS.STREAMS"
```

Why do you have the :colon at the start of the (string) package name? That's what's breaking it. The colon in lisp is a reader macro, much like a the backtick (`) or the comma (,). Any symbol preceded with a colon is interned into a special keyword package. Essentially what is happening is this: lisp thinks the package is called ":COM.BESTINCLASS.STREAMS", but when you try to refer to it as :com.bestinclass.streams, the colon is interpreted as the keyword reader macro, and lisp finds the name of the com.bestinclass.streams symbol in the keyword package, which is of course "COM.BESTINCLASS.STREAMS" *without* the colon.

I would recommed using one notation consistently throughout your program for packages, either use :keywords "STRINGS" or #:uninterned-symbols, but don't mix n' match.

See [this pdf]("http://www.flownet.com/gat/packages.pdf") for everything you could ever want to know about packages (but were afraid to ask :)).

---

### Post by Lau_of_DK on 2008-05-31
Thanks for posting alasdair.


There were a few issues. Firstly, like you said, I should stick to keywords, which I did. Then secondly, I wasnt aware that you had to specify (in-package) after defining it, but of course you do.

And then thats basically it, its working now.

Thanks,
Lau

---

