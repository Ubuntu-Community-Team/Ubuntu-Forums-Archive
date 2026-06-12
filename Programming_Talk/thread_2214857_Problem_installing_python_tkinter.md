---
title: "Problem installing python tkinter"
date: 2014-04-03
forum: Programming Talk
---

### Post by Tom_Carr on 2014-04-03
I am getting this message when I try to install tkinter

tom@tom-OptiPlex-755:~$ apt-get install python-tk
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tom@tom-OptiPlex-755:~$ 

What am I doing wrong?

---

### Post by slickymaster on 2014-04-03
> **Tom_Carr said:**
> I am getting this message when I try to install tkinter

tom@tom-OptiPlex-755:~$ apt-get install python-tk
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), **[COLOR=#ff0000]are you root?[/COLOR]**
tom@tom-OptiPlex-755:~$ 

What am I doing wrong?
The solution is in the error message: **_are you root?_** Use sudo to run the install command with root privileges```
sudo apt-get install python-tk
```

---

### Post by Tom_Carr on 2014-04-03
Thanks.  That did it.

---

### Post by slickymaster on 2014-04-03
You're welcome. Glad you got it fixed.

---

