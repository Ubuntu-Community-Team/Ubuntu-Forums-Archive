---
title: "python doesn't display locale date format"
date: 2007-01-15
forum: Programming Talk
---

### Post by marianom on 2007-01-15
Hi, see this please:

```
mariano@mishima:~/sourcecode/$ date +%x
15/01/07
mariano@mishima:~/sourcecode/$ python
Python 2.4.4c1 (#2, Oct 11 2006, 21:51:02) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import locale
>>> print locale.nl_langinfo(locale.D_FMT)
%m/%d/%y
>>>
```

As you can see with the "date" function, the locale mask for date in my system is dd/mm/yyyy. However when I try it with locale.D_FMT in python it gives me mm/dd/yyyy.
As I read in Python Library Reference (page 721): 
```
D_FMT Return a string that can be used as a format string for strftime(3) to represent a date in a locale-speci&#64257;c way.

```

So I expect the function to return %d/%m/%y. Can you explain me why it's happening?

Thanks in advance

---

### Post by ghostdog74 on 2007-01-15
its doesn't seem to affect me
```

sun:~ # date +%x
01/16/07
sun:~ # python
Python 2.4.2 (#1, May  2 2006, 08:13:46)
[GCC 4.1.0 (SUSE Linux)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import locale
>>> print locale.nl_langinfo(locale.D_FMT)
%m/%d/%y
>>>

```
strange. I am using SUSE btw.

---

### Post by marianom on 2007-01-15
Ok I talked to the guys in the irc channel and they told me -and they were right- that first I need to execute this:
locale.setlocale(locale.LC_ALL, '')

So, now:

```
>>> locale.setlocale(locale.LC_ALL, '')
'es_ES.UTF8'
>>> print locale.nl_langinfo(locale.D_FMT)
%d/%m/%y
>>> 

```

---

