---
title: "pygtk2 windows distribution via py2exe prob"
date: 2008-05-01
forum: Programming Talk
---

### Post by ecs_pf5 on 2008-05-01
Wrote a small python - gtk2 gui app to get my feet wet with linux programming, it worked fine. Just one source file using GTK to fire up a simple GUI and a short bit of scripting to do something - in thi case it downloads a file from the web.

Then decided to try and 'compile' it to run on MS Windows, just to see if I could do it.

Installed all the prerequisites on XP:

python, py2exe, cairo, pygobject, pygtk, gtk2

wrote a setup.py script, ran it, and a /dist/ folder appeared containing a Windows distribution of my app which in the main, works fine :)

Only problem is, after 'compilation' via py2exe, something weird goes AWOL with the character set in the app GUI.

All the button label characters are square boxes, as are any characters in textboxes etc.

However, if I don't compile my source through py2exe, and just run it in the Windows' version of the python interpreter, the GUI comes up perfect (and the program operates flawlessly)

Any guesses as to what could be wrong that's causing the character set to go wonky after py2exe? something in my setup.py? Must admit I didn't really understand too much about the py2exe setup/config script & mine's mainly cut-and-pastery and maybe leaves something important out :(

setup.py:

```

from distutils.core import setup
import py2exe

setup(
name='myapp',
version='1.0',
packages=['myapp'],
scripts=['myapp.py'],

windows=[
{
  'script': 'myapp.py',
}
],

options = {
'py2exe' : {
  'includes': 'cairo, pango, pangocairo, atk, gobject',
},
'sdist': {
  'formats': 'zip',
}
}
)

```













ahhhhhh.... solved.

I discovered a logfile in the /dist/ directory after running the app:




```

C:\Python25\dist\ytdown.exe:510: PangoWarning: No modules found:
No builtin or dynamically loaded modules were found.
PangoFc will not work correctly.
This probably means there was an error in the creation of:
  'C:\Python25\dist\etc\pango\pango.modules'
You should create this file by running:
  pango-querymodules > 'C:\Python25\dist\etc\pango\pango.modules'
C:\Python25\dist\ytdown.exe:510: PangoWarning: failed to find shape engine, expect ugly output. engine-type='PangoRenderWin32', script='latin'
C:\Python25\dist\ytdown.exe:510: PangoWarning: failed to find shape engine, expect ugly output. engine-type='PangoRenderWin32', script='common'
C:\Python25\dist\ytdown.exe:514: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
C:\Python25\dist\ytdown.exe:514: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead

```


after a bit of fiddling this batch file did the trick:


```

cd\
C:
md Python25\dist\etc\pango\
cd GTK
cd bin\
pango-querymodules.exe > C:\Python25\dist\etc\pango\pango.modules

```

---

### Post by gethoper on 2009-02-20
Your solution is working greate!!!! thanks lots!!!

-Billy

---

