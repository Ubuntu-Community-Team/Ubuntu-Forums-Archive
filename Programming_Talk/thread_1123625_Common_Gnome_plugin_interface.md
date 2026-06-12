---
title: "Common Gnome plugin interface?"
date: 2009-04-12
forum: Programming Talk
---

### Post by NintenDave on 2009-04-12
I see a lot of Gnome programs that support plugins, and they all seem to have a very common interface. Is there a library available for Gnome apps to allow easy exposing of an interface to external plugins? If not, should there be one? Is it even possible/feasible?

Thanks.

---

### Post by kknd on 2009-04-12
No (at least I don't think so). But all use gmodule, from glib, a portable abstraction for dynamic library loading.

---

### Post by NintenDave on 2009-04-13
Thanks, GModule looks pretty decent.

---

