---
title: "delete browser history - how?"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by carusoswi on 2008-10-10
How does one go about clearing the browser history?  I am running Kazehakase and also Firefox version 3.03.

I tried deleting kazehakase, but when I reinstalled, the history was still there.

Suggestions would be appreciated.

Thanks.

Caruso

---

### Post by aeiah on 2008-10-10
[http://kazehakase.sourceforge.jp/wiki/?Clearing+cache+and+history](http://kazehakase.sourceforge.jp/wiki/?Clearing+cache+and+history)

---

### Post by fooman on 2008-10-10
in firefox's toolbar,  go to tools > clear private data

in the box that pops up,  just put a check next to the items you wish to clear and click the "clear private data now" button.

---

### Post by aeiah on 2008-10-10
note that if you do it manually and through the GUI, ~/.kazehakase/mozilla/kazehakase/history.dat for example is located in your home directory (that's what ~/ is shorthand for) in the .kazehakase folder (etc). folders starting with a . are hidden. you can toggle whether they're viewable or not using ctrl+h

---

### Post by SteveNorman on 2008-10-10
cntrl-shift-del in firefox

---

### Post by cphan on 2008-10-23
Thanks Aeiah, this was the answer I was looking for.

:KS


> **aeiah said:**
> note that if you do it manually and through the GUI, ~/.kazehakase/mozilla/kazehakase/history.dat for example is located in your home directory (that's what ~/ is shorthand for) in the .kazehakase folder (etc). folders starting with a . are hidden. you can toggle whether they're viewable or not using ctrl+h

---

### Post by hyper_ch on 2008-10-23
is there a specific reason why you want do that?

---

### Post by gjoellee on 2008-10-23
When you have Firefox open pess CTRL + Shift + Delete, and select the things you want to delete in the new window...

---

