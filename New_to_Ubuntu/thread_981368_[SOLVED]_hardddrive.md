---
title: "[SOLVED] hardddrive"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Techarmy on 2008-11-13
ok well my teacher gave me a new hard drive its smaller but use full withit i have 60gb and i need tp know if and how can use both + the smaller 1 has windows but i want it for more space PLZ HELP
edit i might be getting a 120 gb too so im gonna remove the small 1 and use the 120 as master and 40 as slave

---

### Post by bobnutfield on 2008-11-13
Of course you can use both, if it is compatible with your computer.  Just run a partition editor (like gparted) and delete the windows partition if you don't want it.  The it will show up in your system as /dev/sdb.  It can be mounted and you can store files on it, or install a second operating system.  If you are going to use it for storage of Ubuntu files, format it with the ext3 filesystem.

---

