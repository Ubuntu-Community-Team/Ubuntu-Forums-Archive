---
title: "Can't install new language with qt-language-selector"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by BeholdMyGlory on 2008-08-19
When trying to install a new language from system settings in Kubuntu 8.04, nothing happens. So, i ran "sudo qt-language-selector --mode install" from terminal, and got the following output:
```
Traceback (most recent call last):
  File "/usr/bin/qt-language-selector", line 29, in <module>
    lc = QtLanguageSelector(app, "/usr/share/language-selector/", sys.argv[2])
  File "/usr/lib/python2.5/site-packages/LanguageSelector/qt/QtLanguageSelector.py", line 43, in __init__
    self.init()
  File "/usr/lib/python2.5/site-packages/LanguageSelector/qt/QtLanguageSelector.py", line 77, in init
    self.updateLanguagesList()
  File "/usr/lib/python2.5/site-packages/LanguageSelector/qt/QtLanguageSelector.py", line 120, in updateLanguagesList
    languages.sort()
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 1: ordinal not in range(128)
arvid@ubuntu:~$ sudo qt-language-selector --mode install
Traceback (most recent call last):
  File "/usr/bin/qt-language-selector", line 29, in <module>
    lc = QtLanguageSelector(app, "/usr/share/language-selector/", sys.argv[2])
  File "/usr/lib/python2.5/site-packages/LanguageSelector/qt/QtLanguageSelector.py", line 43, in __init__
    self.init()
  File "/usr/lib/python2.5/site-packages/LanguageSelector/qt/QtLanguageSelector.py", line 77, in init
    self.updateLanguagesList()
  File "/usr/lib/python2.5/site-packages/LanguageSelector/qt/QtLanguageSelector.py", line 120, in updateLanguagesList
    languages.sort()
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 1: ordinal not in range(128)
```

I know that I can install the language packs needed with apt-get, but it's confusing a few friends i've recently got to try Linux(Kubuntu).

---

