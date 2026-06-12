---
title: "cdbs: debclean not found"
date: 2007-06-30
forum: Packaging and Compiling Programs
---

### Post by eddymul on 2007-06-30
Following the cdbs docs, I am trying to run cdbs-edit-patch.

Here's what I did:
[LIST=1]
[*]apt-get source python-django
[*]sudo apt-get build-dep python-django
[*]cd python-django*
[*]cdbs-edit-patch mypatch
[/LIST]

I got:
/usr/bin/cdbs-edit-patch: 51: debclean: not found

What should I do next?

What package do I need to install to obtain debclean?

---

### Post by eddymul on 2007-06-30
> **eddymul said:**
> What package do I need to install to obtain debclean?

devscripts

---

