---
title: "[SOLVED] pygtk - show everything in a class"
date: 2008-02-19
forum: Programming Talk
---

### Post by Can+~ on 2008-02-19
So, I've been following the tutorial of pygtk, and decided to start my own application, which was rather simple, but with some tabs ("notebook") on it.

Anyway, when starting, it was easy to "show" elements:
```
self.widget.show()
```

But, as the list grew bigger, I'm having problems managing all the shows, I even tried an array, but it sucked.

So, my question is, if there's a reduced mode to show everything, I tried for instance:
```
for i in dir(self):
  i.show()
```

Produces:
> AttributeError: 'str' object has no attribute 'show'

That won't work, since dir produces a list of strings, not objects, so either (and, btw, I would add a regular expression to that to avoid the __init__ and any other non-gtk thing being dragged into):
[LIST=1]
[*]Convert the string into an object, which I don't know how to do.
[*]Or, another method.
[/LIST]

Any ideas?
Thanks in advance.

---

### Post by Quikee on 2008-02-20
on toplevel widget (for example gtk.Window) do:
window.show_all()


dir(self) won't cut it because dir returns all local variables and functions of a object - one of them is a string. ;)

---

### Post by Can+~ on 2008-02-20
Oh man, that's awesome.

I'm on the chapter 9 of the pygtk tutorial, and still uses the .show() for every widget, maybe this guide is a bit deprecated or something.

Anyway, thanks. [Solved]

---

