---
title: "Server and DB questions"
date: 2009-02-23
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-02-23
i am a server and DB noob so speak english (or 1337 sp3@k) for me please :)

basically i am making an app that goes to a server and pulls data back and then will display it, but i dont know how to get started with the server part

what language should i use (just state a language and reason...it doesnt matter if i know it or not...learning is fun)?

how about the server and SQL part?

---

### Post by cl333r on 2009-02-23
If you're new to this, I'd suggest PHP as being the most common way to go and NetBeans being (arguably) the most intuitive and easy to use IDE, since NetBeans 6.5 supports PHP I'd suggest going this way.
Learn here:
[http://www.netbeans.org/kb/trails/php.html](http://www.netbeans.org/kb/trails/php.html)
Download here:
[http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html)

---

### Post by jimi_hendrix on 2009-02-23
forgot to mention:

i am making a desktop app

---

### Post by Wybiral on 2009-02-23
Pretty much any language will do, provided it can read from a socket. I would still recommend Python though, it's super easy to do something like this in Python (quickly and painlessly).

```

import urllib
print urllib.urlopen('http://www.google.com').read()

```

---

