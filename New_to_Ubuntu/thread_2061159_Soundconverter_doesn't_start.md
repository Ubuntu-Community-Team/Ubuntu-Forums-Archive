---
title: "Soundconverter doesn't start"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by oliverlor on 2012-09-21
Since I have upgraded  to Ubuntu 12.04 (using gnome classic without effects), Soundconverter does not start anymore. I reinstalled it---without a change in result. When I enter 

```
sounconverter
``` 

in a terminal, I get the following response:

 > SoundConverter 1.5.4
Traceback (most recent call last):
  File "/usr/bin/soundconverter", line 46, in <module>
    locale.setlocale(locale.LC_ALL,'')
  File "/usr/lib/python2.7/locale.py", line 539, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

Does anyone what is going wrong resp. how I can start Soundconverter?

A more general question: since I have upgraded to 12.04, I experience a lot of bugs, crashing programs, configuration menus that do not work properly, and so forth, so that I regret to have made this upgrade. Is there a trick to make it work smoother and more stable?

Thanks for any help!

---

### Post by acimi66 on 2012-09-21
When you type "sound converter" into DASH does it show up as a program?

---

### Post by oliverlor on 2012-09-22
Is there a DASH in gnome classic? Soundconverter appears in the Applications menu, and this uses the command "soundconverter %U".The Synoptic Package amnager says Soundconverter is installed.

---

### Post by oliverlor on 2012-09-22
Finally, I found a thread with the same problem (and a solution!). See

[http://ubuntuforums.org/showthread.php?t=1852556](http://ubuntuforums.org/showthread.php?t=1852556)

Thanks!

---

