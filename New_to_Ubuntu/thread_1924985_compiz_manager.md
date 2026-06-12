---
title: "compiz manager"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by spillage2 on 2012-02-13
Hi all.

running 10.04 and hit issues with an update which screwed my kernel. have reinstalled and used my old /home but compiz manager refuses to start. have uninstalled several time and reinstall but still refuses to start up. i am now lost on things to try and any ideas would appreciated.


spill

---

### Post by MG&amp;TL on 2012-02-13
Could you open a terminal and post the output of:

```
ccsm
```

which will help us debug the problem. Thanks.

---

### Post by spillage2 on 2012-02-14
ok this is what I get

```

(process:2650): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 100, in <module>
    import ccm
  File "/usr/lib/python2.6/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 27, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.6/dist-packages/ccm/Constants.py", line 88, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
mark@mark-desktop:~$ 

```Cheers spill.

---

### Post by MG&amp;TL on 2012-02-14
Sorry, no idea at all...would you mind filing a bug?

---

### Post by wildmanne39 on 2012-02-14
Hi, it looks like the answer is in the last post of this thread.
[http://ubuntuforums.org/showthread.php?t=1489601](http://ubuntuforums.org/showthread.php?t=1489601)
Thanks

---

### Post by spillage2 on 2012-02-16
Hi and thanks for all the replies and suggestions...this is driving me mad and still not playing ball.

I have tried 

export LC_ALL="C"

and then

sudo dpkg-reconfigure --force locales

no joy.

checked /etc/default/locale

which shows 

LANG="en_GB.UTF-8"

have also spent a good few hours on google trolling for suggestions and answers but hit a wall..

---

