---
title: "py2exe compiled incorrectly?"
date: 2008-09-04
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2008-09-04
Hi Guys

I have been using py2exe along with python 2.5 on win xp to compile a python program I made but its thrown out a error that I can seem to figure out.

All goes well during the compile but when I go into the 'dist' folder and run the .exe file it complains it can find msvcr71.dll which I can see in the folder and it confirmed to have been included by the py2exe compiler
```
 MSVCP71.dll - C:\Python25\lib\site-packages\wx-2.8-msw-unicode\wx\MSVCP71.dll
```

Anyone have an idea whats happening?

Mike

---

### Post by Zugzwang on 2008-09-04
Note that msvcr71.dll != MSVCP71.dll

Also note that the program loader of windows searches for the .DLLs when starting the application only in the following locations:
[LIST]
[*]Directory the executable is started from
[*]Windows/System32, Windows/System, Windows folder
[/LIST]
So even if it is in some sub-folder, it is *not* found.

---

### Post by Mickeysofine1972 on 2008-09-04
Sorry I typed that wrong I think as the exe is in the same directory as the DLL.

however, I have just this minute found a fix:

```
from distutils.core import setup
import py2exe,sys,os

origIsSystemDLL = py2exe.build_exe.isSystemDLL
def isSystemDLL(pathname):
        if os.path.basename(pathname).lower() in ("msvcp71.dll", "dwmapi.dll"):
                return 0
        return origIsSystemDLL(pathname)
py2exe.build_exe.isSystemDLL = isSystemDLL

... then do the setup call

```

this seems to have done the trick! :D

Thanks for the info though!

Mike

---

