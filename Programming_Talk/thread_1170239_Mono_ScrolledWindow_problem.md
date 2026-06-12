---
title: "Mono ScrolledWindow problem"
date: 2009-05-26
forum: Programming Talk
---

### Post by Dbugger on 2009-05-26
Hi! Im developing in Mono with GTK and i have a TextView widget inside a ScrolledWindow Widget, and sometimes I insert text into the Textview via:

tv.insertatcursor("whatever");

my question is, is is possible to make the window autoscroll down as the text is being inserted?

Thank you!

---

### Post by cszikszoy on 2009-05-26
```

textview1.Buffer.Text = "This is some text in a textview";
textview1.Buffer.PlaceCursor (textview1.Buffer.EndIter);

```

That should help.  GTK# is pretty easy, because it's really just a CLI binding of the C library.  So if you can find documentation for anything in GTK in C (or any other language, really) you can apply the same stuff to GTK#.  The syntax might change a little, but it shouldn't be too hard to figure it out.

---

