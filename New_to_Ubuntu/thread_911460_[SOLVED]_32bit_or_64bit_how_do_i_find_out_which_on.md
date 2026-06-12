---
title: "[SOLVED] 32bit or 64bit? how do i find out which one im using?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by dmurat on 2008-09-05
how can i find out if i am using a 32bit ubuntu or a 64bit?

---

### Post by Thingymebob on 2008-09-05
in a terminal type

uname -a

64 bit currently reads
Linux ------- 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 **x86_64** GNU/Linux

---

### Post by troj on 2008-09-05
> **dmurat said:**
> how can i find out if i am using a 32bit ubuntu or a 64bit?

Use the command:

[INDENT][FONT="Courier New"]/bin/uname -m[/FONT][/INDENT]

You will typically get:

[INDENT][FONT="Courier New"]i686[/FONT][/INDENT]

for 32-bit (maybe 'i586' is an possibility too?), and:

[INDENT][FONT="Courier New"]x86_64[/FONT][/INDENT]

for 64-bit.

---

### Post by dmurat on 2008-09-05
thanks, solved ^^

---

