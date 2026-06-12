---
title: "Python and Samba"
date: 2012-10-08
forum: Programming Talk
---

### Post by martineriksen on 2012-10-08
I am running 12.04 and I have installed the python-samba package, as I want a Python program connect to a SMB/CIFS server. I have been looking high and low for any documentation for this particular package, does anybody here know where to find it?

---

### Post by greenpeace on 2012-10-09
Have you tried running Python from the command line, and using the help() command?

```
gp@mariachi:~$ python
Python 2.7.3 (default, Aug  1 2012, 05:14:39) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import samba
>>> help(samba)
```

---

