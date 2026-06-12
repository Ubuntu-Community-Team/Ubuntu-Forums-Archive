---
title: "Modify Gconf values in any language."
date: 2009-01-02
forum: Programming Talk
---

### Post by unoodles on 2009-01-02
I know that to store preferences in the many GNOME applications use gconf. These values are stored in ~/.gconf.
The actual keys are stored in files called %gconf.xml.
Many languages have gconf bindings, but how would I modify a keys/values in a language without the bindings? Simply modifying the xml files does not work. Is there some way to have gconf re-read the configuration?

Also I would rather not just use a system command to gconftool.

Thanks for the help.

---

### Post by unutbu on 2009-01-02
The python-gconf packake fits the bill.
It even comes with a few examples:
```

/usr/share/doc/python-gconf/examples
/usr/share/doc/python-gconf/examples/simple-controller.py
/usr/share/doc/python-gconf/examples/simple-view.py
/usr/share/doc/python-gconf/examples/basic-gconf-app.py.gz

```

PS: I found this by running
```

apt-cache search gconf
```

and searching the output for "python". You could probably find other language bindings this way too.

---

