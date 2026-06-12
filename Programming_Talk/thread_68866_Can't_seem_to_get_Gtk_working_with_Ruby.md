---
title: "Can't seem to get Gtk working with Ruby"
date: 2005-09-24
forum: Programming Talk
---

### Post by mostwanted on 2005-09-24
Using Hoary, backports enabled.

I've installed the metapackage ruby-gnome2 as the official install guide says, but when I try to run an example script I get this error:

```
./gtk_stuff.rb:2:in `require': No such file to load -- gtk (LoadError)
        from ./gtk_stuff.rb:2
```

Which is weird. Do I have to run it with something else than just *ruby*?

---

### Post by Roptaty on 2005-09-24
[QUOTE=mostwanted]Using Hoary, backports enabled.

I've installed the metapackage ruby-gnome2 as the official install guide says, but when I try to run an example script I get this error:

```
./gtk_stuff.rb:2:in `require': No such file to load -- gtk (LoadError)
        from ./gtk_stuff.rb:2
```

Which is weird. Do I have to run it with something else than just *ruby*?[/QUOTE]
 require 'gtk2'

---

### Post by mostwanted on 2005-09-24
That seemed to do the trick though:

./gtk_stuff.rb:4: uninitialized constant Gtk::WINDOW_TOPLEVEL (NameError)

---

### Post by Roptaty on 2005-09-24
Hmm, the gtk_stuff.rb file isnt by any chance a gtk1 example script, is it?

---

