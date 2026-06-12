---
title: "Error importing Tkinter with Python (  _tkinter )"
date: 2011-03-03
forum: Repositories &amp; Backports
---

### Post by synthmessiah on 2011-03-03
Hello All, 

I want to run Python with Tk, but I am getting the following error: 
```

    # python
    Python 2.7.1 (r271:86832, Mar  1 2011, 10:51:28) 
    [GCC 4.4.5] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import Tkinter
    Traceback (most recent call last):
        File "<stdin>", line 1, in <module>
           File "/usr/local/lib/python2.7/lib-tk/Tkinter.py", line 39, in <module>
                import _tkinter # If this fails your Python may not be configured for Tk
                    [COLOR=Red] ImportError: No module named _tkinter[/COLOR] 

```I've wiped a Dell Optiplex GX620 and installed UBUNTU 10.10. I have  Python 2.7.1 (as can be seen above), and I have Tcl version 8.5: 
```

    # sudo apt-get install Tcl8.5
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Note, selecting 'tcl8.5' for regex 'Tcl8.5'
    Note, selecting 'tcl8.5-dev' for regex 'Tcl8.5'
    Note, selecting 'tcl8.5-doc' for regex 'Tcl8.5'
    Note, selecting 'tcl8.5-kwwidgets' for regex 'Tcl8.5'
    Note, selecting 'tcl8.5-insighttoolkit3' for regex 'Tcl8.5'
    tcl8.5 is already the newest version.
    tcl8.5-dev is already the newest version.
    tcl8.5-doc is already the newest version.
    tcl8.5-insighttoolkit3 is already the newest version.
    tcl8.5-kwwidgets is already the newest version.
    The following packages were automatically installed and are no longer required:
        x11proto-xext-dev x11proto-kb-dev x11proto-render-dev libxrender-dev
        libxdmcp-dev libfontconfig1-dev xtrans-dev x11proto-core-dev
        x11proto-scrnsaver-dev libxext-dev zlib1g-dev x11proto-input-dev
        libfreetype6-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0
        libexpat1-dev tk8.5-dev libxft-dev libx11-dev libxcb1-dev libxss-dev
    Use 'apt-get autoremove' to remove them.
    0 upgraded, 0 newly installed, 0 to remove and 268 not upgraded.

```      
I've installed Tk8.5: 
```

# sudo apt-get install Tcl8.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'tcl8.5' for regex 'Tcl8.5'
Note, selecting 'tcl8.5-dev' for regex 'Tcl8.5'
Note, selecting 'tcl8.5-doc' for regex 'Tcl8.5'
Note, selecting 'tcl8.5-kwwidgets' for regex 'Tcl8.5'
Note, selecting 'tcl8.5-insighttoolkit3' for regex 'Tcl8.5'
tcl8.5 is already the newest version.
tcl8.5-dev is already the newest version.
tcl8.5-doc is already the newest version.
tcl8.5-insighttoolkit3 is already the newest version.
tcl8.5-kwwidgets is already the newest version.
The following packages were automatically installed and are no longer required:
  x11proto-xext-dev x11proto-kb-dev x11proto-render-dev libxrender-dev
  libxdmcp-dev libfontconfig1-dev xtrans-dev x11proto-core-dev
  x11proto-scrnsaver-dev libxext-dev zlib1g-dev x11proto-input-dev
  libfreetype6-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0
  libexpat1-dev tk8.5-dev libxft-dev libx11-dev libxcb1-dev libxss-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 268 not upgraded.

```   
   
I've also installed python-tk, though I'm not sure which version it is ... :confused:
```

# sudo apt-get install python-tk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-tk is already the newest version.
The following packages were automatically installed and are no longer required:
  x11proto-xext-dev x11proto-kb-dev x11proto-render-dev libxrender-dev
  libxdmcp-dev libfontconfig1-dev xtrans-dev x11proto-core-dev
  x11proto-scrnsaver-dev libxext-dev zlib1g-dev x11proto-input-dev
  libfreetype6-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0
  libexpat1-dev tk8.5-dev libxft-dev libx11-dev libxcb1-dev libxss-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 268 not upgraded.

```     
What can I do to get _tkinter installed and seen by Python? 

Thanks in advance! 
-Mike

---

### Post by cgroza on 2011-03-04
In this sample, the import statement is different:
[http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm#AEN50](http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm#AEN50)
It is Tkinter instead, try that.
Also, Tkinter comes by default with python, IDLE is built with it.

---

### Post by synthmessiah on 2011-03-05
> **cgroza said:**
> In this sample, the import statement is different:
[http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm#AEN50](http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm#AEN50)
It is Tkinter instead, try that.
Also, Tkinter comes by default with python, IDLE is built with it.

Hello CGroza,
Thanks for the reply. I'm new to Linux and I didn't know that Python was already installed when I installed Ubuntu 10.10 on a PC at work. Indeed, the issue was a mismatch between the python-tk and the Python-2.7.1 that I installed over the Ubuntu version. 
After removing all Python and re-installing using sudo apt-get install, and doing an update, all was well. 

I have learned not to mix and match unless absolutely necessary! ;-) 

-Mike

---

### Post by cgroza on 2011-03-06
> **synthmessiah said:**
> Hello CGroza,
Thanks for the reply. I'm new to Linux and I didn't know that Python was already installed when I installed Ubuntu 10.10 on a PC at work. Indeed, the issue was a mismatch between the python-tk and the Python-2.7.1 that I installed over the Ubuntu version. 
After removing all Python and re-installing using sudo apt-get install, and doing an update, all was well. 

I have learned not to mix and match unless absolutely necessary! ;-) 

-Mike
You removed python!?!?!?! Didn't your system crash because a lot of services depend on python a lot!!!

---

