---
title: "Django install"
date: 2007-07-24
forum: Programming Talk
---

### Post by cmay4 on 2007-07-24
I am trying to get Django installed, but something is not right.  The apt-get install seems to work fine.  However, when I try to create a project, I get an error about a missing module:

```
$ django-admin.py startproject myproject
Traceback (most recent call last):
  File "/usr/bin/django-admin.py", line 4, in <module>
    import pkg_resources
ImportError: No module named pkg_resources
```Has anyone else seen this?  Thanks.

---

### Post by cmay4 on 2007-09-03
Its been a while, so I will bump this.  I never found a solution and gave up on it.  Anyone else seen this and found a solution?  Seems pretty odd that that the Ubuntu install just doesn't work.

---

### Post by pmasiar on 2007-09-03
ask Django community - they are friendly and quick.

---

### Post by Mirrorball on 2007-09-03
I have Django working, but I downloaded and installed it myself, not from a package.

---

