---
title: "How do I get emacs to use python 3.0?"
date: 2009-01-28
forum: Programming Talk
---

### Post by Jengu on 2009-01-28
I installed python 3.0, but if I press C-c C-c in a buffer it still evaluates it using python 2.x. Anyone know how I get it to use python 3.0? Putting #!/usr/bin/python3 at the top of the file didn't help.

---

### Post by PandaGoat on 2009-01-28
First start python mode: M-x python-mode [enter].  Then customize the python-python-command variable: M-x customize-variable [enter] python-python-command [enter].

---

