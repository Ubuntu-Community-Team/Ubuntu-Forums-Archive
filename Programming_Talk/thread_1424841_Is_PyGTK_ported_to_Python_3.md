---
title: "Is PyGTK ported to Python 3?"
date: 2010-03-08
forum: Programming Talk
---

### Post by __init__ on 2010-03-08
Is PyGTK ported to Python 3?
I googled hard but haven't found clear answer.

---

### Post by Bachstelze on 2010-03-08
Not meaning to be rude, but why don't you ask on the PyGTK mailing lists instead?

---

### Post by __init__ on 2010-03-08
> **Bachstelze said:**
> Not meaning to be rude, but why don't you ask on the PyGTK mailing lists instead?

I should have, to tell you the truth, but I never used mailing lists, and kind of unaccustomed to this.

At first I wanted to ask how to install it in ubuntu since python-gtk package does not include module for py3 but brief investigation of case gave me thought that pygtk may not be ported at all yet.

I actually don't understand all this laziness about moving forth to py3. It may require some work, but all you have to do is to fix some syntax changes and that's all. And in the end everyone will have to switch anyway. Py3 is such a cutie, personally I am looking forward to take it on everyday usage.

---

### Post by Quikee on 2010-03-09
No.. there is no PyGObject for Python 3 (Which is needed for PyGTK) and they don't want to port it for Python 3. The want to drop manually written PyGObject with PyGI that is automatically generated with help of GObject introspection but this library is still in experimental stage. When PyGI matures it will gain support for Python 3. Changing the old manually written PyGObject to support Python 3 would therefore be a wasted efford which is better spend to work on PyGI. 

Python 3 has only syntax changes? Are you kidding? They changed the internal representation of how strings work. This only is such a fundamental change that breaks almost all current bindings.

---

### Post by __init__ on 2010-03-09
Thanks for detailed explanation! It makes sense.

---

