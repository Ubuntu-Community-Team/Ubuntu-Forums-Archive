---
title: "[Python] GPLv3 Compatible?"
date: 2007-09-23
forum: Programming Talk
---

### Post by Nekiruhs on 2007-09-23
I want to know if legally I can license a program I wrote in python under the GPLv3. If my program is GPLv3, does that prohibit me from using LGPL and GPLv2 modules? I don't even know what the core modules, python, and PyGTK are licensed under. Care to enlighten me?

---

### Post by nanotube on 2007-09-23
python itself, and core modules, is licensed under the PSFL (python software foundation license), which is gpl compatible for any gpl version.

if you use any gplv2 licensed modules, though, you /may/ run into incompatibility. if it is licensed under "gpl v 2 or any later version" then you have no problem. but if it is under "gpl v2 only", then they are incompatible. 

as per the following quote from [http://www.gnu.org/philosophy/license-list.html](http://www.gnu.org/philosophy/license-list.html) 
```
Please note that GPLv3 is not compatible with GPLv2 by itself. However, most software released under GPLv2 allows you to use the terms of later versions of the GPL as well. When this is the case, you can use the code under GPLv3 to make the desired combination.
```

as to pygtk, they say they are licensed under the lgpl, without specifying a version - but their site about page links to lgpl v3 ([http://www.pygtk.org/about.html](http://www.pygtk.org/about.html))

which of course is compatible with gpl v3. 

hope that helps. :)

edit: lgpl2.1 is also compatible with gpl3, as per [http://www.fsf.org/licensing/licenses/:](http://www.fsf.org/licensing/licenses/:)
```

This is the previous version of the LGPL: a free software license, but not a strong copyleft license, because it permits linking with non-free modules. It is compatible with GPLv2 and GPLv3.
```

---

