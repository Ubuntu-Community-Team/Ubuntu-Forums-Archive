---
title: "Terminal Navigation"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by Reuben702 on 2011-10-22
I have been trying to install Age of Empires 3 and am following the tutorial here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795&iTestingId=14831](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795&iTestingId=14831)

I have all the DLLs in place but it says to CD to C:\WINDOWS\SYSTEM32
and I am lost at how to do so.
I have tried countless combinations such as:
cd C:/windows/system32
cd /windows/system32
cd windows/system32
cd C:

I am completely lost could you please explain how to navigate there.

---

### Post by dave01945 on 2011-10-22
try this

```
cd ~/.wine/drive_c/windows/system32
```

---

### Post by enkay009 on 2011-10-22
You can get the Linux path by running this:

```
winepath 'C:\Windows\System32'
```

Ignore any errors and just look at the last line.

---

### Post by Reuben702 on 2011-10-22
Thanks helped a lot! :popcorn:

---

