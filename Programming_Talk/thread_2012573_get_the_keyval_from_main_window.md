---
title: "get the keyval from main window"
date: 2012-06-29
forum: Programming Talk
---

### Post by &#968;&#955;&#949;&#960;&#964;&#959; on 2012-06-29
I want to get the keyval from the main window so i wrote this:
```
window = self.builder.get_object("mangar_window")
        keyname = Gdk.keyval_name(window.keyval)
        print keyname
```

but i runs i get 
```
AttributeError: 'MangarWindow' object has no attribute 'keyval
```
i tried with event.keyval in the brackets but i get the same error

any help

---

