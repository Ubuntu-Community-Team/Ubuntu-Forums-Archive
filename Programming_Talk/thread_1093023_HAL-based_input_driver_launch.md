---
title: "HAL-based input driver launch"
date: 2009-03-11
forum: Programming Talk
---

### Post by henryz21651 on 2009-03-11
I have an input driver xyz designed specifically for laptops, and
wish to have HAL launch it the way it launches regular input
driver evdev.  I added this stanza

<match key="system.formfactor" string="laptop">     
         <merge key="input.x11_driver" type="string">xyz</merge>     
</match>

in hal/fdi/preprobe/10osvendor/10-x11-input.fdi.  But it does
not work.  What am I missing here ?

---

