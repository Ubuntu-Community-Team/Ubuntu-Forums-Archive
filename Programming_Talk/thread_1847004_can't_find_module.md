---
title: "can't find module"
date: 2011-09-20
forum: Programming Talk
---

### Post by gishaust on 2011-09-20
hi Ubuntu programmers,

I have been learning python in the Ubuntu terminal but I have come to a stand still. I found a module that works on a key press and from the command line I typed the following

```

work@work:~$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import msvcrt
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named msvcrt
>>> 


```

as you can see I can't import the module. How do I go about finding it and installing this module or any other module?

---

### Post by Bachstelze on 2011-09-20
The msvcrt module is available on Windows only.

[http://docs.python.org/library/msvcrt.html](http://docs.python.org/library/msvcrt.html)

---

### Post by ofnuts on 2011-09-20
> **Bachstelze said:**
> The msvcrt module is available on Windows only.

[http://docs.python.org/library/msvcrt.html](http://docs.python.org/library/msvcrt.html)Yup. MSVCRT=MicroSoft Visual C RunTime (or somesuch).

---

### Post by gishaust on 2011-09-20
Thanks now it makes sense, what would I use in ubuntu

---

### Post by Smart Viking on 2011-09-20
> **gishaust said:**
> Thanks now it makes sense, what would I use in ubuntu
What do you want to do?

---

