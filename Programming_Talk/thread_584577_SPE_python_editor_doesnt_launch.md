---
title: "SPE python editor doesnt launch"
date: 2007-10-21
forum: Programming Talk
---

### Post by hecato on 2007-10-21
Hi there, I have a fresh 7.10 install.

Then I decide install SPE from synaptic and all when OK, but clicking on the menu that display the icon doesnt work.

Then I go to the site [http://pythonide.blogspot.com/](http://pythonide.blogspot.com/) and downloaded it from svn like it says

> svn checkout svn://svn.berlios.de/python/spe/trunk/_spe

it work like this:

```
:~/_spe$ python ./SPE.py 
```

not like this:

```
:~/_spe$ ./SPE.py 
```


Anyway, is more a report that says ey when you install SPE via synaptic it will not run on a fresh 7.10 install.

---

### Post by Pyth on 2007-10-21
I had the same problem with SPE (installed with **apt-get install spe**), being unable to launch it from the Applications menu.  I entered the terminal and entered the "spe" command only for it to fail, as well as warn me that the version of wxPython (that Aptitude installed along with SPE) is not supported with the current version of SPE.

I followed some debug steps it recommended and got the following output:

```

Spe Warning: Spe was developped on wxPython v2.6.1.0., but v2.8.4.0. was found.
If you experience any problems please install wxPython v2.6.1.0.


SPE v0.8.2.a (c)2003-2005 www.stani.be

If spe fails to start:
 - type "python SPE.py --debug > debug.txt 2>&1" at the command prompt
   (or if you use tcsh: "python SPE.py --debug >& debug.txt")
 - send debug.txt with some info to spe.stani.be[at]gmail.com
 

Spe Warning: Spe was developped on wxPython v2.6.1.0., but v2.8.4.0. was found.
If you experience any problems please install wxPython v2.6.1.0.

Blender support disabled (run SPE inside Blender to enable).

Encrypted debugging disabled. 
  If you prefer encrypted debugging, install the "Python Cryptography Toolkit"
  from http://www.amk.ca/python/code/crypto

Spe is running in debugging mode with this configuration:
- platform  : linux2
- python    : 2.5.1
- wxPython  : 2.8.4.0.
- interface : <default>
- encoding  : UTF-8

Launching application...
Create: Framework: menu.
Create: Framework: toolbar.
Create: Framework: statusbar.
Traceback (most recent call last):
  File "/usr/share/pycentral/spe/site-packages/_spe/SPE.py", line 209, in <module>
    style           = style)
  File "/usr/share/pycentral/spe/site-packages/_spe/sm/wxp/smdi.py", line 1278, in __init__
    wx.App.__init__(self,redirect=not debug)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7757, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7354, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/pycentral/spe/site-packages/_spe/sm/wxp/smdi.py", line 1298, in OnInit
    **self.attributes)
  File "/usr/share/pycentral/spe/site-packages/_spe/sm/wxp/smdi.py", line 801, in __init__
    Parent.__init__(self,app=app,page=page,**options)
  File "/usr/share/pycentral/spe/site-packages/_spe/sm/wxp/smdi.py", line 596, in __init__
    **options)
  File "/usr/share/pycentral/spe/site-packages/_spe/sm/wxp/smdi.py", line 325, in __init__
    self.__statusBar__()
  File "/usr/share/pycentral/spe/site-packages/_spe/sm/wxp/smdi.py", line 417, in __statusBar__
    self.statusBar = self.app.StatusBar(parent=self,id=wx.ID_ANY)
  File "/usr/share/pycentral/spe/site-packages/_spe/Menu.py", line 727, in __init__
    self.throbber   = Throbber(self,'throbber_still.gif')
  File "/usr/share/pycentral/spe/site-packages/_spe/Menu.py", line 733, in __init__
    GIFAnimationCtrl.__init__(self,statusBar,-1,info.imageFile(fileName))
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/animate.py", line 242, in __init__
    self.LoadFile(filename)
  File "/usr/share/pycentral/spe/site-packages/_spe/Menu.py", line 746, in LoadFile
    if fileName != self._fileName and not self._running:
AttributeError: 'Throbber' object has no attribute '_fileName'
```

I was a bit surprised that this was the case as I would've thought packages were actually made to be compatible with the version of dependencies installed.

**a.strotman** posted a patch over at [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/spe/+bug/124896"), but I was more fond of your method of just running the Subversion code.

So I did like you did (first uninstalling SPE and thereby python-wxgtk2.8) and got the current version from the Subversion trunk, ran the command and it launched nicely.  I did get one error when I launched it, though, but I'm unsure of what it means:

```
(python:6738): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed
```

Thanks for posting this solution, I'm sure it will help many.  I hope the package gets fixed.

---

### Post by geirha on 2007-10-21
When you run it with ./SPE.py, your shell (probably bash) interprets it. And since python code isn't a bash-script (obviously), bash will fail. You can tell the shell that it should be run by python though, by adding the special operator #! at the first line of the file. Typically it should be:
```
#!/usr/bin/env python
```

Sounds like SPE.py lacks this first line, or the path to the python binary is wrongt.

---

### Post by hecato on 2007-10-21
In fact, *SPY.py* doesnt contain that line, **but** the file that contain that line is only *spe* at

spe file contain only the following lines:

```
#!/usr/bin/env python

import _spe.SPE

```


The first lines of SPE.py
```
import sys

if sys.platform.startswith('win') and sys.executable.lower().endswith('pythonw.exe'):
    from cStringIO import StringIO
    sys.stdout = StringIO()

MIN_WX_VERSION  = '2.5.4.1'
GET_WXPYTHON    = 'Get it from http://www.wxpython.org!'

try:
    import wxversion
    wxversion.ensureMinimal(MIN_WX_VERSION)
```


Unnable to run properly in SVN version.

[LIST]
[*]If you make executable spe and double click on it, it will nor work.
[*]If you make executable SPE.py also will not work (probably by what say geirha).[/LIST]Correct ways to launch it?
[LIST]
[*]Open a terminal and in the directory _spe type **python SPE.py**
[*]Make a script file **run.sh** and add the line python **SPE.py**[/LIST]That will work, you dont need to open the terminal, but making a direct access will not work (right click on run.sh->make link), thus you need modify run.sh like this

```
cd /home/tyoc/_spe
python SPE.py
```
ya the working directory where it is launch matter a lot. Now you are ready for add a link and move in to Desktop, taskbar or watever, also you can make now a personal launcher (where you insert applets in the panel) and launch run.sh from there (instead of the link).


-----------------


By the way I havent at the moment uninstalled SPE or changed any versions that synaptic install about wx python versions, SVN it work with what was install here and apparently dont conflict with SPE installed from synaptic (thought this will not be launch correctly).

---

### Post by stani on 2007-10-25
> **geirha said:**
> When you run it with ./SPE.py, your shell (probably bash) interprets it. And since python code isn't a bash-script (obviously), bash will fail. You can tell the shell that it should be run by python though, by adding the special operator #! at the first line of the file. Typically it should be:
```
#!/usr/bin/env python
```

Sounds like SPE.py lacks this first line, or the path to the python binary is wrongt.

Thanks, I added that:
$ svn commit -m "fixed: add environment to SPE.py (linux)"
[email]stani@svn.berlios.de[/email]'s password: 
Sending        SPE.py
Transmitting file data .
Committed revision 272.

---

### Post by ricnar456 on 2007-10-25
In install SPE with the instructions and when i try run say wxpython is not installed, and i go to synaptic and choose wxpython and is not here, how i can install the correct version of wxpython for SPE

~/_spe$ python SPE.py
Error: SPE requires wxPython, which doesn't seem to be installed.
Get it from [http://www.wxpython.org](http://www.wxpython.org)!


ricnar

---

### Post by ricnar456 on 2007-10-25
is solved i install wxpython with instructions of the page and work perfect thanks.

ricnar

---

### Post by hecato on 2007-10-25
In my case, I dont uninstalled nothing (even the SPE that doesnt run).

Directly to the point, a simple way to run the subversion (in my case) whould be[LIST=1]
[*]Open synaptic[LIST]
[*] in configuration->preferences click in suggestions as dependencies  (not necessary, but sometimes helpful)[/LIST] 
[*]search SPE package and click to install it (direct dependencies would be installed, also suggestions if you selected in configuration->preferences that option)
[*]Click OK for the extra packages
[*]then search again SPE and don't install it, click apply changes, and you will have all dependencies installed
[*]go and fetch the SVN version of SPE 
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe[/LIST]You are done.

---

### Post by stani on 2007-10-25
> **hecato said:**
> In my case, I dont uninstalled nothing (even the SPE that doesnt run).

Directly to the point, a simple way to run the subversion (in my case) whould be[LIST=1]
[*]Open synaptic[LIST]
[*] in configuration->preferences click in suggestions as dependencies  (not necessary, but sometimes helpful)[/LIST] 
[*]search SPE package and click to install it (direct dependencies would be installed, also suggestions if you selected in configuration->preferences that option)
[*]Click OK for the extra packages
[*]then search again SPE and don't install it, click apply changes, and you will have all dependencies installed
[*]go and fetch the SVN version of SPE 
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe[/LIST]You are done.

I wouldn't recommend this method. You will end up with older versions of wxGlade. Before getting the source from subversion, you only need to do:

```
sudo apt-get install subversion python-wxgtk2.8
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe
```

See also:
[http://pythonide.blogspot.com/2007/02/how-to-download-latest-spe-from_26.html](http://pythonide.blogspot.com/2007/02/how-to-download-latest-spe-from_26.html)
[https://bugs.launchpad.net/ubuntu/+source/spe/+bug/124896](https://bugs.launchpad.net/ubuntu/+source/spe/+bug/124896)

---

### Post by hecato on 2007-10-25
Oh, I see my error.

Thx for the links!!!

---

### Post by hecato on 2007-10-25
Extra question, if I have more than 1 open file, now to navigate in them without use mouse?


I have try the keyboard short cuts but it link to [http://pythonide.stani.be/manual/html/manual12.html](http://pythonide.stani.be/manual/html/manual12.html) which is not available, thus [http://web.archive.org/web/20061117161228/http://pythonide.stani.be/manual/html/manual12.html](http://web.archive.org/web/20061117161228/http://pythonide.stani.be/manual/html/manual12.html) none seem to be what I'm searching.

---

### Post by stani on 2007-10-25
There is no shortcut for that.

---

### Post by CostaRica on 2007-11-04
> **stani said:**
>  ...you only need to do:

```
sudo apt-get install subversion python-wxgtk2.8
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe
```



Sorry but...after reading everything what I did was:

1. Uninstall SPE and the wxGlade I had installed through synaptic
2. Run
```
sudo apt-get install subversion python-wxgtk2.8
```

3. Then run
```
 svn checkout svn://svn.berlios.de/python/spe/trunk/_spe
```


Now...How do I run it?

Sorry if I seem like a retarded, but I am doing my best to run from M$.

---

### Post by CostaRica on 2007-11-04
Anyone there? Dump.

---

### Post by CostaRica on 2007-11-04
Can anybody tell me what am I doing wrong?  Thanks

---

### Post by geirha on 2007-11-05
After running that svn checkout command, you should have a directory called _spe in the directory you ran it from. The file you want to run is _spe/SPE.py. Run it with ```
python _spe/SPE.py
``` Alternatively, you can make the file executable with ```
chmod +x _spe/SPE.py
``` or by right-click file -> properties -> permissions in nautilus, at which point you can run it directly with ```
_spe/SPE.py
``` or by double-clicking it in nautilus.

---

### Post by CostaRica on 2007-11-05
Thanks a lot!

---

### Post by stani on 2008-01-31
Hi, the best way to use SPE is still from subversion. However I fixed the older spe version in synaptic for Feisty and Gutsy. Now I need your help. Enable in System>Software Sources Feisty-proposed or Gutsy-proposed. Afterwards install spe:
sudo apt-get update
sudo apt-get install spe

Spe should now work. Please confirm in a comment on launchpad  that this worksso this fix is for everyone and can move from proposed to the normal repostiories:
[https://bugs.launchpad.net/bugs/124896](https://bugs.launchpad.net/bugs/124896)

After this test, you can disable the proposed repositories again.

Thanks a lot!
Stani

---

### Post by seventhc on 2008-01-31
works for me, already entered it into launchpad. :D

---

### Post by stani on 2008-02-01
> **seventhc said:**
> works for me, already entered it into launchpad. :D
Thanks to all, the fix has been uploaded to launchpad for Gutsy. Any Feisty testers still around here? Please test and report on launchpad.

Stani

---

