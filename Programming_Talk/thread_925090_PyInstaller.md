---
title: "PyInstaller"
date: 2008-09-20
forum: Programming Talk
---

### Post by hosseinyounesi on 2008-09-20
Hi every body, I'm going to make an executable from this code :
[PHP]
import sys
from PyQt4 import QtGui
app = QtGui.QApplication(sys.argv)
widget = QtGui.QWidget()
widget.resize(250, 150)
widget.setWindowTitle('simple')
widget.show()
sys.exit(app.exec_())
[/PHP]

It converts it completely, but when I want run it, There is an error :
[PHP]
Traceback (most recent call last):
  File "<string>", line 2, in <module>
ImportError: cannot import name QtGui
[/PHP]
What I have to do !?!?!?!!?!?!?!?!
Linux : Ubuntu
Python2.5
Thanks

---

### Post by Zugzwang on 2008-09-20
Dear OP (original poster),

[LIST]
[*] You have ran into the problem that some files are missing on your system. This can be seen more or less directly from the error message. Since Ubuntu uses package management, it is worthwhile searching for a package containing that file. In order to do so, redirect your web browser to "http://packages.ubuntu.com", type in the name of the file you are missing (note that the error message may contain parts of paths special to your system, like your home path if it is searched for the missing file there - make sure to strip them beforehand) in the section "Search the contents of packages", select "packages that contain files whose names contain the keyword" and choose your distribution. Then hit search and have a look at the answers. You should get a list of packages containing a respective file. Examine the package names and remember the names of the packages that look promising. Then install them by entering "sudo apt-get install " plus a space-separated list of packages in the terminal. You will need "sudo"-rights for this. Afterwards, see if your problem has vanished. If not, come back reporting what you did (including what you actually searched for) and ask for further help.
[*] Please make sure to describe your problem as precise as possible. Your explanations are a little bit hard to understand:
  [LIST]
  [*]"It converts it completely" - What converts what to what? Python is normally interpreted, not compiled, so we cannot know what you mean by this.
  [/LIST]
[/LIST]

---

### Post by Rocket2DMn on 2008-09-20
hosseinyounesi, please do not create duplicate threads - I have jailed your second one.  It is not fair to those trying to help you, and doesn't actually help solve your problem any faster.  In fact, people are less likely to help you if they see duplicates.  Thank you.

---

### Post by pmasiar on 2008-09-20
OP, read "how to as questions" in my sig

---

### Post by hosseinyounesi on 2008-09-23
Oh, sorry if I didn't ask my question clearly, Also it was just a MISTAKE that I sent 2 threads about a matter !!!
I want to make a binary package from a python .py file with "pyinstaller" in ubuntu. Anyone worked with this program ? 
[Sorry for my bad english]

---

### Post by pmasiar on 2008-09-23
What you are trying to accomplish?

Making "installer" which is able to run independently of runtime is something tricky, because Python is not designed to work that way (Python is not C). "Normal" mode of operation is to install the runtime and then copy/distribute a script. If you need native installer for Python modules, look at ez_install.py

---

