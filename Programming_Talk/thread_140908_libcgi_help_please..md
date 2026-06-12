---
title: "libcgi help please."
date: 2006-03-07
forum: Programming Talk
---

### Post by zootreeves on 2006-03-07
I'm just trying to compile the 'simple form' example from the libcgi-doc package and i get the following error:

```
 In function `main':form1.c:(.text+0x31): undefined reference to `cgi_init'
:form1.c:(.text+0x36): undefined reference to `cgi_init_headers'
:form1.c:(.text+0x53): undefined reference to `cgi_include'
:form1.c:(.text+0x5f): undefined reference to `cgi_include'
:form1.c:(.text+0x6b): undefined reference to `cgi_include'
:form1.c:(.text+0x7c): undefined reference to `cgi_end'
collect2: ld returned 1 exit status
make: *** [all] Error 1

```

My hello world cgi example using libcgi does not compile either. I have installed all packages with reference to anything cgi and also downloaded the libcgi source.

---

### Post by zootreeves on 2006-03-07
Ok got it working now, cgilib seems to conflict with it

---

