---
title: "Tk8.5.4 install fail"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by MRM0607 on 2008-10-10
Dear Forum users,

I am trying to install Tcl/Tk on ubuntu 8.04 LTS.

[COLOR="Blue"]Prior to installing I did not know that this is available via package manager.[/COLOR]

I installed Tcl 8.5.4 (which works) but when I tried to install Tk 8.5.4 the config file gave following error 

configure:2742: result: gcc -E
configure:2766: gcc -E  conftest.c
configure:2772: $? = 0
configure:2804: gcc -E  conftest.c
conftest.c:9:28: error: ac_nonexistent.h: No such file or directory
configure:2810: $? = 1
configure: failed program was:
| /* confdefs.h.  */


configure:7242: $? = 0
configure:7245: test -s conftest.o
configure:7248: $? = 0
configure:7334: gcc -c  -pipe  conftest.c >&5
conftest.c: In function 'main':
conftest.c:28: error: storage size of 'buf' isn't known
configure:7340: $? = 1
configure: failed program was:
| /* confdefs.h.  */

but ends with 0 code. I tried make after that but it fails.

My question is:

[COLOR="Blue"]Can I just install Tk8.5.4 via package manager?
[/COLOR]
when tried it tries to install both Tcl8.5.4 and Tk8.5.4.

If I just let it install I am not sure if I might have trouble with already installed Tcl8.5.4.

Thank you.
Mamta Mohan

---

### Post by sumguy231 on 2008-10-10
It should be fine as long as it can find where Tcl was installed to, but if you want you can first check if Tcl8.5.4 has an uninstall option in the makefile it comes with. Try 'make remove' or 'make uninstall'. Or read the makefile. If that works you can install it from the repositories.

---

### Post by MRM0607 on 2008-10-10
> **sumguy231 said:**
> It should be fine as long as it can find where Tcl was installed to, but if you want you can first check if Tcl8.5.4 has an uninstall option in the makefile it comes with. Try 'make remove' or 'make uninstall'. Or read the makefile. If that works you can install it from the repositories.

Thank you.

I will try that. 

Would you have any idea why config file have error and why make failed?

I am new to the whole thing and besides doing work also want to understand the origin of errors.

I would appreciate your response.

Thank you.
mrm0607

---

### Post by sumguy231 on 2008-10-10
Sorry, I don't know other than that obviously it couldn't find some headerr file and there was a compiler error. I've never compiled Tcl/Tk before.

---

