---
title: "[PyGTK]My application wont work after installing!"
date: 2009-07-04
forum: Programming Talk
---

### Post by j7%&lt;RmUg on 2009-07-04
Ok iv finally come to here after trying maybe 30 different things over about 9 hours.

The problem is that i have an application that i made with PyGTK right, it works when i go to run it with:

```
python nameofmyapp.py
```

But not when i use the setup.py install script i made to install it. All it does is install fine and then it wont show up in the gnome menu or run through the terminal.

I think its because im not including something in setup.py or my .desktop file.

Here is my setup.py file:

```
#!/usr/bin/env python

from distutils.core import setup
from distutils.cmd import Command
from distutils.command.install_data import install_data
from distutils.command.build import build
from distutils.log import warn, info, error, fatal
import os
import sys
import platform

setup(name='PyTask',
	version='0.1.0',
	description='Task list manager',
	long_description='A simple task list manager but with extra features designed for developers, programmers and teams.',
	author='Ryan Macnish',
	author_email='nisshh@hotmail.com',
	maintainer='Ryan Macnish',
	maintainer_email='nisshh@hotmail.com',
	license='GNU GPL v3',
	url='http://www.launchpad.net/pytask',
	download_url='https://launchpad.net/pytask/+milestone/0.1.0',
	packages=['pytasklib'],
	package_data={'pytasklib':['pytask.glade']},
	data_files=[
		('/usr/local/share/applications', ['data/pytask.desktop']),
		('/usr/local/share/pixmaps', ['data/icons/48x48/pytask.png']),
		],
)
```

and my .desktop file:

```
[Desktop Entry]
Name=PyTask
Comment=Task list manager
Exec=pytask
Icon=pytask.png
Terminal=false
TryExec=pytask
Type=Application
Categories=GNOME;GTK;Utility;
StartupNotify=false
Name[en_AU]=PyTask
```

If someone could help me figure this out i would appreciate it.

Thanks in advance.

---

### Post by j7%&lt;RmUg on 2009-07-06
Bump.

Anyone have any ideas? What im really stuck on is that i cant get my application to show up in the gnome menu even though i have a .desktop file, i do think that im putting it in the right place at installation time.

I also am unsure as to how to get it so that i can type the name of my application into the terminal and get it to start that way after installation.

I reall do need help with this as iv already tried google.

---

### Post by Can+~ on 2009-07-06
How about trying on the "/usr/share/applications" folder?

I see installed stuff there, and the /usr/local/share/applications being empty.

---

### Post by j7%&lt;RmUg on 2009-07-06
Already tried that. I really dont know what i must be missing here.

Thanks for trying, got any other suggestions?

---

### Post by days_of_ruin on 2009-07-06
You need to install a python script in /usr/bin. The way you have it right now is just a python library. You should have a bin/ folder in the root of your project (same folder as your setup.py) and have your python program in that.

And then add this to your setup(...)
```
scripts=[os.path.join("bin", "rss-notify")]
```

---

### Post by j7%&lt;RmUg on 2009-07-07
Yep i have one questions:

Why do i need the rss-notify part?

I added a bin directory into the directory where my setup.py and i added my python application into there along with its glade file. But now it comes up with this error when i run setup.py through the terminal:

```

error: bin: Is a directory

```

any ideas?

---

### Post by j7%&lt;RmUg on 2009-07-09
Bump, does anyone have any other ideas?

---

### Post by j7%&lt;RmUg on 2009-07-12
Bumb, i still cant figure this out!!

---

