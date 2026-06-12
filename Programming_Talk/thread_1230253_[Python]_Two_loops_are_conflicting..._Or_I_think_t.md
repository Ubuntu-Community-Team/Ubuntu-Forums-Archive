---
title: "[Python] Two loops are conflicting... Or I think they are."
date: 2009-08-03
forum: Programming Talk
---

### Post by ToyImp on 2009-08-03
[http://pastebin.com/d4890bc21](http://pastebin.com/d4890bc21) - for the code.

I'm guessing that I have the two loops conflicting because when I switch the socket setup and gtk setup loops one of them work but not both. How can I fix this?

---

### Post by benj1 on 2009-08-03
whats the exact problem?

i can only see one loop, although i cant see a way for it to exit

---

### Post by Tony Flury on 2009-08-03
the call to "gtk.main()" is effectively a loop - as it defines the GTK event handler loop.


The problem is that you do a "while 1:" in an event handler - which will of course interrupt your gtk event loop.

you need to use :

```

while gtk.events_pending() :
    gtk.main_iteration_do()

```
every so often - this will keep the gtk queue ticking

---

