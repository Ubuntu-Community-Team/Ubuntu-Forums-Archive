---
title: "switching libraries"
date: 2008-01-23
forum: Packaging and Compiling Programs
---

### Post by spamalot on 2008-01-23
Hi All,

I have installed gcc v-4.2 with synaptic manageer but gcc --v shows it's still gcc v4.1. how do i ensure gcc v-4.2 is the default?

thanks!

---

### Post by geraldm on 2008-01-25
The version style may vary a bit, depending on the distribution.
/usr/bin/cc and /usr/bin/gcc are usually links to /etc/alternatives/gcc
The proper compiler would normally be installed to /usr/bin/gcc-4.2
Then the proper way to select the default compiler is to create a link to /usr/bin/gcc-4.2 and put it in /etc/alternatives/gcc

Gerald

---

