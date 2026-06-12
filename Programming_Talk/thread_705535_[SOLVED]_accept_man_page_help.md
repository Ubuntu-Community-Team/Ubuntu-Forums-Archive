---
title: "[SOLVED] accept man page help"
date: 2008-02-23
forum: Programming Talk
---

### Post by spyder0080 on 2008-02-23
hello all,

I'm currently trying to do socket programming for one of my classes and I wanted to look up the man page for accept(), but the result I got was not the one I wanted; the accept() I got was "accept jobs sent to a destination". 
I installed the posix man pages via synaptic, so I should be able to access it. I tried "man accept(2)" but I got an error saying "bash: syntax error near unexpected token `('"

How am I supposed to access this man page (or any other man pages for functions that have multiple uses, like open()?)

thanks!

---

### Post by jeffus_il on 2008-02-23
Sometimes using google is easier than installing the man page:
[http://linux.die.net/man/2/accept](http://linux.die.net/man/2/accept)

Also I think your command should have been```
 man 2 accept
```

---

### Post by spyder0080 on 2008-02-23
I checked to see if I forgot to install any man pages, and I found out that I didn't install the manpages-dev package.

After installing that, I tried the command you suggested and it worked! Thanks!

---

