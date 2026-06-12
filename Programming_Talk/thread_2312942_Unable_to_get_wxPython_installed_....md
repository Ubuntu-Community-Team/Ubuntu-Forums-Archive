---
title: "Unable to get wxPython installed ..."
date: 2016-02-08
forum: Programming Talk
---

### Post by Rick_Astley on 2016-02-08
I ran the following command:

sudo apt-get install python-wxgtk2.8 python-wxtools wx2.8-i18n libwxgtk2.8-dev libgtk2.0-dev

and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
libwxgtk2.8-dev is already the newest version.
python-wxgtk2.8 is already the newest version.
python-wxtools is already the newest version.
wx2.8-i18n is already the newest version.

In my Python code I have:

#!/usr/bin/env python
try:
    import wx
except ImportError:
    print('wxpython is not installed')

and when I run that program I get:

wxpython is not installed

 ..... am I missing something here???

---

### Post by spjackson on 2016-02-08
I suspect that
```

#!/usr/bin/env python

```
is running python 3 but the above packages are for python 2.

---

### Post by Rick_Astley on 2016-02-08
Thank you for replying.  How can I check what 
#!/usr/bin/env python

is running?

---

### Post by Rick_Astley on 2016-02-08
At the terminal I ran the shown in my opening post, but this time using "python2.7" instead of "python3.4" and now it's working!  Thank you!

---

