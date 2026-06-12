---
title: "error message when trying to use gcalcli"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-04-24
anyone else getting this error messsage

ray@ray-Latitude-D630:~$ gcalcli calm
Traceback (most recent call last):
  File "/usr/bin/gcalcli", line 392, in <module>
    class gcalcli:
  File "/usr/bin/gcalcli", line 410, in gcalcli
    dateParser    = DateTimeParser()
  File "/usr/bin/gcalcli", line 335, in __init__
    self.pdtCalendar = parsedatetime.Calendar();
  File "/usr/lib/python2.7/dist-packages/parsedatetime/__init__.py", line 216, in __init__
    self.ptc = Constants()
  File "/usr/lib/python2.7/dist-packages/parsedatetime/__init__.py", line 1733, in __init__
    self.locale = pdtLocales['icu'](self.localeID)
  File "/usr/lib/python2.7/dist-packages/parsedatetime/pdt_locales.py", line 151, in __init__
    self.icu = pyicu.Locale(localeID)
icu.InvalidArgsError: (<type 'icu.Locale'>, '__init__', (None,))
ray@ray-Latitude-D630:~$

---

### Post by Danger_Monkey on 2014-04-24
I believe this is a confirmed bug in Gcalcli.  I dug around in the code, sure it was a python issue I hadn't seen, but it fails when there are no arguments.  Looking....  Here it is:  [https://bugs.launchpad.net/ubuntu/+source/gcalcli/+bug/1309570](https://bugs.launchpad.net/ubuntu/+source/gcalcli/+bug/1309570)

---

### Post by rburkartjo on 2014-04-24
tks danger . must be particular just to ubuntu because gcalcli works fine on my usb stick that has solydxx installed. will wait for the fix.

---

