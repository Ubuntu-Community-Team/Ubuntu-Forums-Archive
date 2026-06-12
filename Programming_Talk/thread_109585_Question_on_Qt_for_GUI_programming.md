---
title: "Question on Qt for GUI programming"
date: 2005-12-28
forum: Programming Talk
---

### Post by racermike1967 on 2005-12-28
Hi, I am interested in designing GUI's using the Qt development software I don't know how to install it.  Can anyone help me?

---

### Post by asimon on 2005-12-29
For Qt3:
```

sudo apt-get install libqt3-mt-dev qt3-designer qt3-dev-tools qt3-doc qt3-qtconfig qt3-examples qt3-assistant
```
(If you don't want the examples or documentation, then leave that out. The first three are mandatory.)

If you want to use some other language as C++, then you need to install a binding too, like for python 'python-qt3' and 'python-qt3-doc'.
Use 'apt-cache search qt3' to see what other qt3 packages exist, or search via synaptic.

If you want to use Qt4, then I recomment to download the Qt4 source from [TrollTech](http://www.trolltech.com/download/qt/x11.html) and compile it yourself. The Qt4 in Breezy is rather old.

---

