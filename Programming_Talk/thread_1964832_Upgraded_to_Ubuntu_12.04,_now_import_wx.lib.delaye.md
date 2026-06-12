---
title: "Upgraded to Ubuntu 12.04, now import wx.lib.delayedresult fails"
date: 2012-04-24
forum: Programming Talk
---

### Post by Kurtosis on 2012-04-24
I just upgraded from 11.10 Desktop to 12.04 Desktop final beta (sudo do-release-upgrade -d).  So far it's brilliant, and have only hit one relatively show-stopper problem.

[Tribler]("http://tribler.org") depends on the lib [python-wxgtk2.8]("http://www.wxpython.org/"), which was installed under 11.10 and is still installed under 12.04.  However, Tribler fails on startup because it can't import [wx.lib.delayedresult]("http://www.wxpython.org/docs/api/wx.lib.delayedresult-module.html"):

```

$> less /tmp/kurtosis-tribler.log
Traceback (most recent call last):
  File "Tribler/Main/tribler.py", line 27, in <module>
    from Tribler.Main.vwxGUI.MainFrame import FileDropTarget
  File "/usr/share/tribler/Tribler/Main/vwxGUI/__init__.py", line 10, in <module>
    from Tribler.Main.Utility.GuiDBHandler import onWorkerThread, startWorker
  File "/usr/share/tribler/Tribler/Main/Utility/GuiDBHandler.py", line 6, in <module>
    from wx.lib.delayedresult import SenderWxEvent, SenderCallAfter, AbortedException,\
ImportError: No module named delayedresult

```

The specific code that throws this error in */usr/share/tribler/Tribler/Main/Utility/GuiDBHandler.py*:
```

#Written by Niels Zeilemaker
#Extending wx.lib.delayedresult with a startWorker method which uses single producer
#Additionally DelayedResult is returned, allowing a thread to wait for result

import wx
from wx.lib.delayedresult import SenderWxEvent, SenderCallAfter, AbortedException,\
    DelayedResult, SenderNoWx
...

```

When I try to do the import manually in the Python interpreter it fails there as well:

```

$> python
Python 2.7.3 (default, Apr 20 2012, 22:39:59) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import wx
>>> from wx import DelayedResult
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: cannot import name DelayedResult
>>> import wx.lib.delayedresult
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named delayedresult

```

But I can verify that the module is installed, is where it seems it should be, and contains the required class DelayedResult:

```

$> less /var/lib/dpkg/info/python-wxgtk2.8.list|grep delayed
/usr/share/pyshared/wx-2.8-gtk2-unicode/wx/lib/delayedresult.py
/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/lib/delayedresult.py
$> locate delayedresult.py
/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/lib/delayedresult.py
/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/lib/delayedresult.pyc
/usr/share/pyshared/wx-2.8-gtk2-unicode/wx/lib/delayedresult.py

```

```

$> less /usr/share/pyshared/wx-2.8-gtk2-unicode/wx/lib/delayedresult.py|grep DelayedResult
only requirement on consumer is that it must accept a DelayedResult instance 
    'Handler', 'DelayedResult', 'Producer', 'startWorker', 'PreProcessChain')
    simply added as attribute whenever a DelayedResult is created. 
        delayedResult = DelayedResult(result, jobID=self.__jobID)
        exception will be raised when DelayedResult.get() is called."""
        delayedResult = DelayedResult(extraInfo, 
class DelayedResult:
        """You should never have to call this yourself. A DelayedResult
...

```

So, why does every import fail?

Fwiw, uname and apt-cache info:

```

$> uname -a
Linux hp-dm1-4050us 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
```

$> apt-cache show python-wxgtk2.8
Package: python-wxgtk2.8
Priority: optional
Section: universe/python
Installed-Size: 21815
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: wxWidgets Maintainers <freewx-maint@lists.alioth.debian.org>
Architecture: amd64
Source: wxwidgets2.8
Version: 2.8.12.1-6ubuntu2
Replaces: libwxgtk2.6-0-python, wxpython2.6-0
Provides: python2.7-wxgtk2.8
Depends: python-wxversion (>= 2.6.3.2.2-2), python2.7, python (>= 2.7.1-0ubuntu2), python (<< 2.8), libc6 (>= 2.14), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), libwxbase2.8-0 (>= 2.8.12.1), libwxgtk2.8-0 (>= 2.8.12.1)
Suggests: wx2.8-doc, wx2.8-examples, editra
Conflicts: libwxgtk2.6-0-python, python-wxaddons, wxpython2.6-0
Filename: pool/universe/w/wxwidgets2.8/python-wxgtk2.8_2.8.12.1-6ubuntu2_amd64.deb
Size: 5377032
MD5sum: a4d8749cf60fef528b4cf8fb4e4c12bc
SHA1: 8426efaefc88e4c20133b18f77d97279e869c961
SHA256: d565aa69ae9972aa8a3a768c21d7d3920071e576dd8807f5876b760d9b95b8a6
Description-en: wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
 wxWidgets (formerly known as wxWindows) is a class library for C++ providing
 GUI components and other facilities on several popular platforms (and some
 unpopular ones as well).
 .
 This package provides a Python binding to the wxGTK library and the
 wxPython runtime support libraries.
Homepage: http://www.wxpython.org/
Description-md5: 512d862ab885e743c6f3b61ad713b1a9
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: edubuntu-desktop-gnome, ubuntustudio-graphics

```

---

### Post by Kurtosis on 2012-04-25
Update:  Google only had one relevant link with the error "ImportError: No module named delayedresult":

[https://bugs.launchpad.net/keryx/+bug/503056](https://bugs.launchpad.net/keryx/+bug/503056)

Looks like the error could be caused with the wrong version of wxPython or multiple versions.

I checked and found two versions, python-wxgtk2.6 and python-wxgtk2.8.  Uninstalld 2.6, and the tribler startup error changed to:

```

Traceback (most recent call last):
  File "Tribler/Main/tribler.py", line 27, in <module>
    from Tribler.Main.vwxGUI.MainFrame import FileDropTarget
  File "/usr/share/tribler/Tribler/Main/vwxGUI/__init__.py", line 5, in <module>
    import wx
ImportError: No module named wx

```

```

$> aptitude search python-wxgtk
p   python-wxgtk2.6                                                     - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)                  
p   python-wxgtk2.6:i386                                                - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)                  
p   python-wxgtk2.6-dbg                                                 - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding, debug version)   
p   python-wxgtk2.6-dbg:i386                                            - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding, debug version)   
i   python-wxgtk2.8                                                     - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)                  
p   python-wxgtk2.8:i386                                                - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)                  
i   python-wxgtk2.8-dbg                                                 - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding, debug version)   
p   python-wxgtk2.8-dbg:i386                                            - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding, debug version)   

```

Now it can't find the entire wx module.  No idea what's going on here.

---

### Post by Kurtosis on 2012-04-25
Fixed it, woohoo!  The problem is that */usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/* is not in Python's sys.path for some reason.  

```

>>> import sys
>>> print sys.path

```

Adding that location to $PYTHONPATH in .profile adds it to sys.path and allows Tribler to start, at least for the current user.

```
export PYTHONPATH="$PYTHONPATH":/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/
```

Now just gotta figure out why that location is no longer in sys.path on 12.04.

---

### Post by holzbrenner on 2012-04-29
I had a similar problem with another python-based program after upgrade to 12.04 ("ImportError: No module named wx"). I fixed the problem by re-installing package python-wxversion (Mark for Reinstallation in Synaptic Package Manager). I suppose installing this package adds python-wxgtk location to sys.path.

---

### Post by Kurtosis on 2012-04-29
Thanks, I tried something similar - complete uninstall and reinstall of all wx related files - python-wxgtk2.6, python-wxgtk2.8, python-wxversion (only reinstalled second two, left 2.6 out).  Still no luck though.  

Then figured out I could add the missing library to PYTHONPATH.  A bit of a kluge since that only works for the current user, but since this is my laptop it's not a big deal.  Yours is better if it works though.

---

### Post by MadCow108 on 2012-04-29
whats the content of /usr/lib/wx/python/wx2.8.pth?
it should direct python to search wx-2.8-gtk2-unicode

---

### Post by Kurtosis on 2012-04-30
> **MadCow108 said:**
> whats the content of /usr/lib/wx/python/wx2.8.pth?
it should direct python to search wx-2.8-gtk2-unicode
Looks right:

```
$> cat /usr/lib/wx/python/wx2.8.pth
wx-2.8-gtk2-unicode
```

---

### Post by MadCow108 on 2012-05-01
do you have python-wxgtk2.6 installed?
if yes remove it and reinstall python-wxgtk2.8 and python-wxversion

---

### Post by Kurtosis on 2012-05-04
> **MadCow108 said:**
> do you have python-wxgtk2.6 installed?
if yes remove it and reinstall python-wxgtk2.8 and python-wxversion

Did that above already.  Uninstalled all three, then reinstalled only python-wxgtk2.8 and python-wxversion.  No luck :(

---

### Post by rasmusscholer on 2012-09-11
I had the same issue, also after updating to 12.04. (Well, I was initially having problems importing wx.aui, which was caused by my python installation using wx2.6 and not wx2.8---but the cause of that is that wx2.8 was not found by my python...) I think this is caused by the python-wxgtk2.8 installation using the directory /usr/lib/wx/python/ for the path files (.pth). My python installation, like yours, did not recognize this directory. However I solved it in a slightly different way.

I copied the wx2.8.pth (and wx.pth symlink) from /usr/lib/wx/python/ to /usr/local/lib/python2.7/dist-packages/ -- This is also where the wx-2.8-gtk2-unicode folder is also located! After that, the problem was solved. 

This issue is likely caused by changing directory standards between different versions of python-wx included in the different distributions (11.10 vs 12.04).

---

