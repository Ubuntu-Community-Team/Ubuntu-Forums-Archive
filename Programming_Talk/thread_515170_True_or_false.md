---
title: "True or false?"
date: 2007-08-01
forum: Programming Talk
---

### Post by w1nD on 2007-08-01
You can use a base class pointer to point to a derived class object since you may not know which derived class type to use until runtime.

True or false?

---

### Post by aks44 on 2007-08-01
True. This is a part of what is called **polymorphism** (see also: **virtual** functions).

---

### Post by pmasiar on 2007-08-01
... and this is the whole point why we bother with OOP in the first place.

---

### Post by Rocket2DMn on 2007-08-01
Indeed, as long as you only call functions/methods available to this base class.

---

