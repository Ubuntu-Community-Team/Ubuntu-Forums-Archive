---
title: "Faild to find &lt;linux/string.h&gt;"
date: 2006-11-22
forum: Programming Talk
---

### Post by bjorna on 2006-11-22
I try to build a driver that include 
[COLOR="Red"]<asm/io.h>[/COLOR]
that includes 
[COLOR="Red"]<asm-i386/io.h>[/COLOR] 
that includes 
[COLOR="Red"]<linux/string.h>[/COLOR] (/usr/inlude/linux/string.h) 
that is missing! The only string I found is in /usr/inlude/string.h.

Is there something I do not understand?

I run Edgy (6.10)

Hope to get some advise.

/Björn

---

### Post by Carlos Santiago on 2006-11-22
try include only <string>

---

### Post by amo-ej1 on 2006-11-22
On any random kernel source you can easily find the string.h in 
*/usr/src/linux-$version/include/linux/string.h* perhaps your include path settings are wrong ? Or you are looking in the wrong place ;-) Didn't find them in /usr/include/linux/ either.

---

