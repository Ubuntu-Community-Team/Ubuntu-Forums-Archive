---
title: "HOWTO: Convert from Visual Basic to Python"
date: 2007-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Garyu on 2007-02-04
Paul Paterson is a great guy who wrote an application to automatically convert Visual Basic code to Python. There is both a command-line tool and a GUI. Here is how you install it in 10 simple steps:

**1. We need to solve some dependencies:**
```
sudo apt-get install pythoncard python-simpleparse
```

**2. Download the command-line tool (and the GUI) from SourceForge:**
[http://sourceforge.net/project/showfiles.php?group_id=79297](http://sourceforge.net/project/showfiles.php?group_id=79297)

**3. Unpack these files (just right-click and choose "Unpack here" - or double-click to open and drag-and-drop).**

**4. Open a terminal and change directory to the command-line tool** 
```
cd <where you extracted it>/vb2py-0.2.2
```

**5. Install the command-line tool**
```
sudo python setyp.py install
```

**6. Change directory to the GUI application**
```
cd <where you extracted it>/vb2pygui-0.2.2
```

**7. Install the GUI**
```
sudo python setup.py install
```

**8. Create a desktop launcher (shortcut)**
* Right-click your desktop 
* Choose "Create Launcher"
* Name: vb2py (or whatever you see fit)
* Command: python /usr/lib/python2.4/site-packages/vb2pygui/vb2pyGUI.pyw
* Choose a nice icon, click OK

**9. Start vb2pyGUI by double-clicking your launcher on the desktop**

**10. Load your VisualBasic project file (*.vbp)**

If you need more information and documentation, visit the project home page:
[http://vb2py.sourceforge.net/](http://vb2py.sourceforge.net/)

---

