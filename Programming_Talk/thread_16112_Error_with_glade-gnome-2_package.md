---
title: "Error with glade-gnome-2 package"
date: 2005-02-19
forum: Programming Talk
---

### Post by blixtra on 2005-02-19
I've installed glade-gnome-2 and since then I get this Error dialog everytime I install or remove packages:

```
E: libtool:  subprocess post-installation script returned error exit status 1
E: gnome-common:  dependency problems - leaving unconfigured
E: glade-gnome-2:  dependency problems - leaving unconfigured
```

Glade seems to work fine but the dialog is quite annoying.

I'm on Hoary with all updates. Anybody have a clue what's wrong here and how to fix  it. I'm not an apt-get expert just yet ;) ...but it seems to be a problem with the libtool pkg.

Chris

---

### Post by randy on 2005-02-20
One of the dependencies for glade-gnome-2 currently isn't available.  There's probably other output further on your terminal.

---

### Post by blixtra on 2005-02-20
Seems a bit odd to me that I'm able to actually use Glade if a dependence is missing.  If this were the case shouldn't it refuse to install?

Perhaps I'm unsderstanding something wrong.

Chris

---

