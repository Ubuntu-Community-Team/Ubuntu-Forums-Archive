---
title: "Wine issues and dll's"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by KPatrick on 2008-08-01
I'm trying to install a windows based html editor with Fiesty.

I opened the terminal, moved to the folder location and entered 

wine filename.extension

from here I got an error saying that I was missing two dll files.
- MSVCP60.DLL
- mfc42.dll

I then went and dl'd them, and placed them in the Windows directory of .wine

so I re-entered my command of wine filename.extension

I was greeted with this error:
wine: Call from 0xafb32a to unimplemented function MFC42.DLL.6571, aborting

Any suggestions would be helpful.  Thanks.:confused:

---

### Post by Pconfig on 2008-08-01
Did you try looking up your program here?:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

You can mostly find whether or not your app works with wine (if it's a popular one)

---

