---
title: "Locale not supported by C library"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by spe05081 on 2008-06-08
I keep getting these errors in the terminal:

Locale not supported by C library
What's going on???

For example:
.....................................
thomasps@COLIBRI:~$ sudo nautilus
[sudo] password for thomasps:
(nautilus:7364): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(nautilus:7364): Gdk-WARNING **: locale not supported by C library
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:7364): WARNING **: Unable to add monitor: Operation not supported
.....................................
**OR (after installing CompizConfig Settings Manager (ccsm)):**
.....................................
thomasps@COLIBRI:~$ ccsm

(ccsm:7940): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 39, in <module>
    import ccm
  File "/usr/lib/python2.5/site-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.5/site-packages/ccm/Conflicts.py", line 26, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.5/site-packages/ccm/Constants.py", line 89, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.5/locale.py", line 478, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
.....................................

---

### Post by omi291 on 2008-06-08
trying typing in "gksudo nautilus" instead of sudo nautilus and tell what happens

As for Compiz, I can't help there :(...i'm still relatively new to ubuntu myself

---

### Post by spe05081 on 2008-06-08
Same thing:

thomasps@COLIBRI:~$ gksudo nautilus

(gksudo:16765): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(nautilus:16766): Gdk-WARNING **: locale not supported by C library
Initializing nautilus-share extension

---

### Post by cariboo on 2008-06-09
Check your timezone and language setting by entering the following in a terminal:

```
sudo dpkg-reconfigure locales
```

Can't tell where from but for North America set for en-us

Jim

---

### Post by spe05081 on 2008-06-10
> **cariboo907 said:**
> Check your timezone and language setting by entering the following in a terminal:

```
sudo dpkg-reconfigure locales
```

Can't tell where from but for North America set for en-us

Jim

Just tried here is the result:
==================================
thomasps@COLIBRI:~$ sudo dpkg-reconfigure locales
[sudo] password for thomasps: 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
====================================
Looks like there is something missing here.  I live in (English) Canada, so my locale should be set to that, if not US. Any clue as to how to fix this?

---

