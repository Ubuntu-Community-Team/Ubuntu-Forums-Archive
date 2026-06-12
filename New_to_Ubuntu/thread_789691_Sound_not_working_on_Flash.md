---
title: "Sound not working on Flash"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-05-10
Sound is not working on Flash through Firefox 3b5 through Ubuntu 8.04. Youtube is what I have tried. I am on ALSA with the HDA Intel driver. Sound is fine, except in Flash. Here is some useful info from about:plugins:

[IMG]http://img329.imageshack.us/img329/7899/plugins1ak8.png[/IMG]

[IMG]http://img147.imageshack.us/img147/8378/plugin2ux7.png[/IMG]

---

### Post by joshsmith on 2008-05-10
install package libflashsupport

---

### Post by linkmaster03 on 2008-05-10
Thanks, that worked!

---

### Post by joshsmith on 2008-05-10
i should mention you may possibly see increase crashes due to a bug in adobe's flash package (out of the hands of ubuntu devs)

the issue is currently being worked on, but is the reason why libflashsupport is not installed by default. 

(as a workaround, if you have no other programs playing any sounds you can have sound in flash without libflashsupport, but this isnt ideal. We need to go and bug adobe!)

---

