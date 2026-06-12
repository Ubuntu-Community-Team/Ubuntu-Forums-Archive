---
title: "Anjuta doesn't seem to recognise devhelp"
date: 2010-12-29
forum: Programming Talk
---

### Post by fopetesl on 2010-12-29
Lucid 10.04  - all updates installed.
```
~$ dpkg -l devhelp*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  devhelp        2.30.0-0ubuntu A GNOME developers help program
ii  devhelp-common 2.30.0-0ubuntu common files for devhelp and its library

~$ dpkg -l anjuta*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  anjuta         2:2.30.1.0-0ub A GNOME development IDE, for C/C++
ii  anjuta-common  2:2.30.1.0-0ub A GNOME development IDE, for C/C++ - data fi
```

Anjuta manual states Shift+F1 will give context help but not for me. :(

What have I (not) done?

---

