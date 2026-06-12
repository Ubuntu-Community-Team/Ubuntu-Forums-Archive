---
title: "jedit cant find fonts"
date: 2007-02-01
forum: Programming Talk
---

### Post by nephish on 2007-02-01
lo there all, 
i downloaded a couple of fonts that i like for scripting. after i did a 
fc-cache 
eclipse, scribes, gedit and other apps load them up nice, but jedit does not.
anything i can do here ?

thanks

---

### Post by hamoda on 2007-02-21
Seems jEdit does not look for installed fonts but has it's own font folder. You can copy the desired fonts as root to */usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/fonts* and restart jEdit. This should work.

---

### Post by nephish on 2007-02-21
indeed , that worked. thanks

---

