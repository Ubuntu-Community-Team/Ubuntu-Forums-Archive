---
title: "how can i generate a c code from glade  3.4.0?"
date: 2008-02-11
forum: Programming Talk
---

### Post by @vijay@ on 2008-02-11
i used glade 2 before and it has an option to generate a c code of the interface
but how can i do this in glade-3???
thanx in advance

---

### Post by shifty2 on 2008-02-11
That feature was removed from glade 3 as the developers felt it was a bad idea to create generated code.

---

### Post by lnostdal on 2008-02-11
yeah, and they are right .. it's a very bad idea

generate xml (data) using glade, then use something like this to load it (your gui) into your program

i do not know if this is 100% correct, but here is an old writing of mine: [http://nostdal.org/ubuntu-programming3.pdf](http://nostdal.org/ubuntu-programming3.pdf) .. (the finished one got lost in a hardware crash)

( [http://nostdal.org/ubuntu-programming1.pdf](http://nostdal.org/ubuntu-programming1.pdf) and [http://nostdal.org/ubuntu-programming2.pdf](http://nostdal.org/ubuntu-programming2.pdf) is also there )

---

