---
title: "use of g_signal_connect_swapped() in gtk"
date: 2008-07-19
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-19
i just started gtk to find troubles in the signal-slot system here.
i cant undertand why do we use this function - g_signal_connect_swapped ; what advantages does it give over g_signal_connect ...and where should i use it over g_signal_connect ??
the manual i am reading says :
> g_signal_connect_swapped() is the same as g_signal_connect() except that the instance on which the signal is emitted and data will be swapped when calling the handler.
the book also says (for g_signal_connect_swapped)
> They are usually used to call a GTK function that accepts a single widget or object as an argument, when a signal is emitted on some other object
i cant understand this line perfectly, though they have given an example..hope someone helps me  better.

---

### Post by loell on 2008-07-19
this might help, [http://markmail.org/message/3wl3wjlgip4v6bzj#query:g_signal_connect_swapped()+page:1+mid:3wl3wjlgip4v6bzj+state:results]("http://markmail.org/message/3wl3wjlgip4v6bzj#query:g_signal_connect_swapped()+page:1+mid:3wl3wjlgip4v6bzj+state:results")


if you're just starting out in gtk programming, don't use complicated callback binders, just use the basic ones.

---

### Post by kknd on 2008-07-19
I use it for my Lua binding of GTK. Its useful because of the varargs.

---

