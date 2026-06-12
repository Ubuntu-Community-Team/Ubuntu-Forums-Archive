---
title: "[SOLVED] Override Tkinter Close"
date: 2008-03-18
forum: Programming Talk
---

### Post by themusicwave on 2008-03-18
Good morning everyone,

Well I forgot my copy of Programming Python at home today.  So I am wondering if some of you could be a reference for me.

All I need to do is override the close event of a TK frame.  The problem is I can't remember the name of th event to bind on.  Through searching I can't find anything.  I wish I knew where some good TK documents where.

So how do I bind to the close event so I can do a proper close?

Also, is there a good TK reference online that I don't know about?

---

### Post by LaRoza on 2008-03-18
> **themusicwave said:**
> 
Also, is there a good TK reference online that I don't know about?

References and Docs: [http://wiki.python.org/moin/TkInter](http://wiki.python.org/moin/TkInter)

Events are at the bottom: [http://infohost.nmt.edu/tcc/help/pubs/tkinter/](http://infohost.nmt.edu/tcc/help/pubs/tkinter/)

(Don't know the answer, sorry)

---

### Post by themusicwave on 2008-03-18
I guess to clarify, what I want to do is perform a check on the form close event.

Then if the program isn't done I will warn the user and ask if they want to quit.

On something like Java I would just hook into the event for closing.

---

### Post by stevescripts on 2008-03-18
Do your sanity check on WM_DELETE_WINDOW ...

along the lines of:
```
 toplevel.protocol("WM_DELETE_WINDOW", callback)

```

where callback is your sanity check.

Hope this helps.

Steve

---

### Post by themusicwave on 2008-03-18
> **stevescripts said:**
> Do your sanity check on WM_DELETE_WINDOW ...

along the lines of:
```
 toplevel.protocol("WM_DELETE_WINDOW", callback)

```

where callback is your sanity check.

Hope this helps.

Steve

That was exactly what I needed.  Thanks!

---

