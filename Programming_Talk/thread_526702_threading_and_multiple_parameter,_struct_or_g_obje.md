---
title: "threading and multiple parameter, struct or g_object?"
date: 2007-08-15
forum: Programming Talk
---

### Post by loell on 2007-08-15
to c gtk coders,

when you do threading, whether it be pthread or gthread , you are only allowed to pass single parameter, right? And if the method called in the threading requires more than one,  you normally had to define a struct and then pass it as parameter.

but how about passing a **G_Object** using **g_object_set_data** to embed those multiple parameters in the method that is being invoked the thread creation?

thoughts?

---

### Post by slavik on 2007-08-15
with pthread, use struct, since then you don't need to be dependent on glib for one thing ... unless you are already using it in which case, you should use gthread IMO.

---

