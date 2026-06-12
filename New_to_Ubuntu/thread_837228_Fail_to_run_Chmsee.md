---
title: "Fail to run Chmsee"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-22
All i get when i click on the icon is a little egg timer and then nothing. When i run in Terminal, i get this error message though;

chmsee: error while loading shared libraries: libxul.so: cannot open shared CT file: No such file or directory

I dont find libxul.so in Synaptic either. How to solve this problem

---

### Post by omi291 on 2008-06-22
take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=781074](http://ubuntuforums.org/showthread.php?t=781074)

---

### Post by wariskampar on 2008-06-22
still no luck even after following the instruction on the link. Any alternative?

---

### Post by qgfreire on 2008-07-13
> **wariskampar said:**
> still no luck even after following the instruction on the link. Any alternative?

If it continues interesting after so long:
1st rm the ln created
2nd do the same ln but taking care to point to the correct xulrunner-1.9/ directory

With me it worked fine!
X's

---

### Post by wariskampar on 2008-07-13
> **qgfreire said:**
> If it continues interesting after so long:
1st rm the ln created
2nd do the same ln but taking care to point to the correct xulrunner-1.9/ directory

With me it worked fine!
X's

Matter of fact, it's still not working. I don't understand what/which ln to rm. Do you mind to explain further

---

### Post by loell on 2008-07-13
why painfully setup/run chmsee when there is still the trusty **xchm**? ;)

let chmsee fix itself in intrepid , until then use xchm.

---

### Post by wariskampar on 2008-07-14
Yeah! For many week, at last found the solution. Thanks loell:)

---

### Post by loell on 2008-07-14
your welcome sir. :)

---

