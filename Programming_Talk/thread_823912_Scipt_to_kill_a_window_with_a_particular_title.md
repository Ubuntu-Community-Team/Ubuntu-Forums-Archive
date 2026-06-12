---
title: "Scipt to kill a window with a particular title"
date: 2008-06-09
forum: Programming Talk
---

### Post by DBQ on 2008-06-09
Hi everybody.  Is there some command available to kill a window with a particular title?  For example, I want to write a script which kills the window titled "test" regardless of whether it is open in firefox, seamonkey etc.  Any suggestions?

---

### Post by ryanhaigh on 2008-06-09
The command you want is wmctrl, although it doesn't kill the windows but closes it gracefully. Its available in ubuntu repos and the man page can give you details or you might want to check out this page: [http://jrandomhacker.info/Wmctrl_examples](http://jrandomhacker.info/Wmctrl_examples)

To close a window titled test you would use [code]wmctrl -c -r "test"

---

### Post by DBQ on 2008-06-09
Thank you.  I will give it a try and tell you how it went.

---

