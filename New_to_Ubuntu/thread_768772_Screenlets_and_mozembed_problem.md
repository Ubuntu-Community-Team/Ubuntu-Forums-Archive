---
title: "Screenlets and mozembed problem"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by asdfqwert on 2008-04-26
When the screenlets manager opens, i get a 

> You need Gtkmozembed to run this Screenlet , please install it


error.I've tried installing some mozembed files from synaptic, and googling "mozembed screenlets" but i don't know where to find it.

---

### Post by Riffer on 2008-04-26
It would help if you let us know what screenlet you are trying to enable.  Its looking for a library of some sort.  I used the search function in synaptic and got a group of different libraries, I have libxul0d and libxul-comman installed on my comp.

---

### Post by shomati_sen on 2008-04-26
Hi, I installed python-gnome2-extras and libxul0d. Now screenlets works well with various google gadgets and is actually useful to me. 

Hope this helps,

Shomati

---

### Post by itsjustarumour on 2008-04-28
> **shomati_sen said:**
> Hi, I installed python-gnome2-extras and libxul0d. Now screenlets works well with various google gadgets and is actually useful to me. 

Hope this helps,

Shomati

I was getting this message as soon as I tried to open Screenlets.  Installing python-gnome2-extras fixed it - thanks shomati_sen!

Cheers,

itsjustarumour

---

### Post by muckblit on 2009-02-28
I have ubuntu intrepid and screenlet ITV does not work. It needs gtkmozembed.

dpkg --list '*embed*'
un  python-gtkmozembed     <none>                 (no description available)

sudo apt-get install python-gtkmozembed

Package python-gtkmozembed is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-gtkmozembed has no installation candidate

Hmmmmmmm.

I have libxul0 and python-gtk2-*

Clicking in ITV just does not cause anything so I can't debug it.

---

### Post by muckblit on 2009-02-28
and I also have python-gnome2-extras and dev versions

---

### Post by josephb on 2009-10-17
:)python-gnome2-extras! HFY!

Much thanks.  I was bangin my head off the wall after synaptic showed that I DID have pythongtk-mozembed installed and my AWN Pandora applet still would not work.

---

