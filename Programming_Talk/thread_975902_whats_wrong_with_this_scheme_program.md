---
title: "whats wrong with this scheme program?"
date: 2008-11-08
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-08
heres the code ```
(begin (display "hello world") (newline))
```

heres the error

```
default-load-handler: expected a `module' declaration for `hello', found: something else in: #<path:/home/vincent/hello.scm>

```

---

### Post by jimi_hendrix on 2008-11-09
nobody?

---

### Post by CptPicard on 2008-11-09
That is neither a function or value definition or a function evaluation ("function call") (EDIT: gah, strike the last one)... it would work straight in the REPL but not when you're reading in source seems like.

---

### Post by jimi_hendrix on 2008-11-09
so how about ```
(define hello (lambda () (display "hello world"))) (begin (hello))
```

---

### Post by CptPicard on 2008-11-09
Looks very contrived and like an infinite loop to me, if it does do something at all :)

If you are after a function that prints Hello World...

```

; first define function
(define (hello)
  (display "Hello World"))

;call it
(hello)

```

Btw, "begin" is not nearly as important as you seem to think... you really just use it as a syntactic aid to group side-effects before a value when you have a need for that in some circumstances.

---

### Post by jimi_hendrix on 2008-11-09
still getting ```
me@my-laptop:~/programs/Scheme$ mzscheme hello.scm
default-load-handler: expected a `module' declaration for `hello', found: something else in: #<path:/home/vincent/programs/Scheme/hello.scm>
```

---

### Post by CptPicard on 2008-11-09
Oh... mzscheme probably expects you to declare a module in your source file. Check the docs. :)

---

### Post by jimi_hendrix on 2008-11-09
> **CptPicard said:**
> Oh... mzscheme

why what do you use...(beside repl)

---

### Post by CptPicard on 2008-11-09
Mit-scheme mostly...

---

### Post by jimi_hendrix on 2008-11-09
where might i find it?

---

### Post by CptPicard on 2008-11-09
In the repositories...

However, I would suggest you figure out what kind of module declaration mzscheme wants, that would probably be easier.

---

### Post by jimi_hendrix on 2008-11-09
so im one step closer...figured out i need mzscheme -f <file name> but now i get ```
 lib: standard-module-name-resolver: collection not found: "scheme" in any of: (#<path:/home/vincent/.plt-scheme/4.0/collects> #<path:/usr/lib/plt/collects>) in: (lib "scheme/init")
hello.scm:2:0: compile: bad syntax; function application is not allowed, because no #%app syntax transformer is bound in: (#%top-interaction define (hello) (display "Hello World"))

```

---

### Post by nvteighen on 2008-11-09
It's interesting: that program should work on the REPL and on a module without any issue... at least with MIT/GNU Scheme.

MIT/GNU Scheme gives you less non-standard stuff, an Emacs-like editor called Edwin, Emacs-integration and very good documentation. Also, it's the implementation used on SICP book/videos.

In Ubuntu Hardy:
```

sudo apt-get install mit-scheme mit-scheme-doc

```

(The docs will be installed at /usr/share/doc/mit-scheme-doc)

After that, you'll have to follow these steps to get it work: [http://ubuntuforums.org/showthread.php?t=778034](http://ubuntuforums.org/showthread.php?t=778034)

In Ubuntu Intrepid, MIT/GNU Scheme doesn't work because of a broken dependency. You won't even be able to compile it from source, unless you get libtdl3 (and its dependencies) from somewhere. It's one of the reasons why I changed to Debian.

---

### Post by jimi_hendrix on 2008-11-09
getting ```
configure: running /bin/bash './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
Unknown machine type: none
configure: error: /bin/bash './configure' failed for compiler

```

---

