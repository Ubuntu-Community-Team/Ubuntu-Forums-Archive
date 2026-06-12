---
title: "Installing CCTBX module for Python"
date: 2008-02-01
forum: Programming Talk
---

### Post by almightymaster on 2008-02-01
I'm running Ubuntu 7.10 Gutsy Gibbon x64 and trying to install CCTBX, a module for Python which is useful for crystallography. It does not feature in Synaptic, unfortunately.

An installation which is supposedly entirely scripted is available at [http://cci.lbl.gov/cctbx_build/show_results.cgi](http://cci.lbl.gov/cctbx_build/show_results.cgi) , but when I run it (having installed csh), it seems to just create a load of directories of pyc files and other stuff without actually registering their existence with Python, or moving it to the Python extensions directory.

I have tried sudo-ing and moving it to the /usr/lib/python2.5/site-packages/ directory myself, but this seems to have no effect either.

Any ideas?!

Ta!

---

### Post by pmasiar on 2008-02-02
This looks like really obscure package. Try contacting developers list, failing that, the author. For such obscure package, s/he could be excited that there are users - or maybe package was abandoned long time ago and you will save yourself wasted time and grief.

---

### Post by almightymaster on 2008-02-04
It is quite obscure, unless you're a crystallographer. Was more wondering if anyone had any generic Python module installation tips...where are the files meant to go? Do they need to be registered in some way for Python to acknowledge their presence?

---

### Post by almightymaster on 2008-02-07
> **almightymaster said:**
> It is quite obscure, unless you're a crystallographer. Was more wondering if anyone had any generic Python module installation tips...where are the files meant to go? Do they need to be registered in some way for Python to acknowledge their presence?

...anyone?

---

### Post by dwblas on 2008-02-07
> without actually registering their existence with PythonAFAIK there is no "registering" in Python.  The program's path has to either be in $PYTHONPATH or you have to append it to the path in whatever program you are writing, and then import these programs.  Beyond that, there is very little that one can tell from what you have said.  You'll have to give more detail on what you are doing to run/import the programs.

---

