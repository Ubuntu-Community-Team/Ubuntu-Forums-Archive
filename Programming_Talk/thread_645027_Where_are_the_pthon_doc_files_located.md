---
title: "Where are the pthon doc files located?"
date: 2007-12-19
forum: Programming Talk
---

### Post by Harvs on 2007-12-19
Hi

Should be an easy one...!
I've just installed python2.5-doc using synaptic. But I've no idea where to find the files (I've looked in /usr/share and then the python folders, but no joy)

cheers

---

### Post by geirha on 2007-12-19
This will list all the files installed by the package ```
dpkg -L python2.5-doc
```

---

### Post by vambo on 2007-12-19
In your terminal, try:

```
pydoc -g
```

---

### Post by LaRoza on 2007-12-19
/usr/share/doc/python

[file:///usr/share/doc/python/html/index.html](file:///usr/share/doc/python/html/index.html)

---

### Post by Harvs on 2007-12-19
Great, thanks guys - found it in

/usr/share/doc/python2.5/html

I like the
```
 dpkg -L
```
command - I've always wondered how you find stuff if it doesn't add a shortcut.
Thanks!

---

### Post by LaRoza on 2007-12-19
The link above would have taken you to it. And the command, pydoc -g would have given a gui for it. (In case you were wondering what the many answers meant)

---

