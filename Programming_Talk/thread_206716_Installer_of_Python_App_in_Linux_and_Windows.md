---
title: "Installer of Python App in Linux and Windows"
date: 2006-06-30
forum: Programming Talk
---

### Post by krypto_wizard on 2006-06-30
I recently wrote a small app using wxPython. It is meant to be run on Windows and Linux both. In Windows I have created the exe as given in py2exe.org guidelines.


What is the Linux equivalent of it ? I am assuming you just make your .py file executable by doing this. Please correct me if I am wrong.
```

chmoad a+x file_name.py

```

What do I need to do in Linux if I need to distribute to people using Linux who don't have all the dependent libraries installed in their Linux distro ?? How can I make a installer kind of thing in Linux which will take care of the dependencies ?

Every help is appreciated.

Thanks

---

### Post by dabear on 2006-06-30
[QUOTE=krypto_wizard]
What do I need to do in Linux if I need to distribute to people using Linux who don't have all the dependent libraries installed in their Linux distro ?? How can I make a installer kind of thing in Linux which will take care of the dependencies ?

Every help is appreciated.

Thanks[/QUOTE]
The package names would be different dependant on which distro you are using.  You would have to use something like:
```

failures = []

try:
    import MyFreakinModule
except ImportError:
    failures.append('FreakinModule')
try:
    import MyFreakinModule2
except ImportError:
    failures.append('OtherFreakinModule')
(...)

if failures:
    print 'these modules have to be installed before continuing, please install:',\
           ', '.join(failures)



```

---

