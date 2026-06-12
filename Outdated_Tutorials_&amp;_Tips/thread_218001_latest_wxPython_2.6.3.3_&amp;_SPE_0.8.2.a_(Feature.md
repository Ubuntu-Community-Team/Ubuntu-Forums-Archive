---
title: "latest wxPython 2.6.3.3 &amp; SPE 0.8.2.a (Feature rich Python IDE)"
date: 2006-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by stani on 2006-07-18
[URL="http://pythonide.stani.be/screenshots/spe-ubu-dapper"][IMG]http://pythonide.stani.be/screenshots/tmb-ubu-dapper[/IMG]
Click for bigger screenshot[/URL]

[More screenshots here...]("http://pythonide.stani.be/screenshots")

The following thread is obsolete. To install SPE just do:

```
sudo apt-get install python-wxversion spe
```

The following thread remains for archiving purposes only.

[SIZE="5"]**Introduction**[/SIZE]

wxPython is a free GUI toolkit for the Python programming language. It allows Python programmers to create programs with a robust, highly functional graphical user interface, simply and easily. On Ubuntu it uses GTK. I'd like to thank Robin Dunn, the author of wxPython, to make this all possible. 

I've written [SPE]("http://pythonide.stani.be"), a python IDE with auto-indentation, auto completion, call tips, syntax coloring, UML viewer, syntax highlighting, class explorer, source index, auto todo list, sticky notes, integrated pycrust shell, python file browser, recent file browser, drag&drop, context help, ... A special feature is [SPE]("http://pythonide.stani.be")'s ability to run interactively inside blender with a 3d object browser.
[SPE]("http://pythonide.stani.be") integrates with XRCed (GUI designer) and ships with wxGlade (GUI designer), PyChecker (source code doctor), Kiki (regular expression console) and WinPdb (remote, multi-threaded debugger). [SPE]("http://pythonide.stani.be") runs on Windows, Linux and Mac OS X.

First make sure you have the pythonX.X-dev package installed. In case you don't have do this in the terminal:
```
$sudo apt-get install python2.4-dev
```

[SIZE="5"]**wxPython**[/SIZE]

> :KS If you are only interested in SPE, you don't need the latest wxPython. You can skip this step safely. Just use the one of the Dapper repository:
```
$sudo apt-get install python-wxgtk2.6 python-wxtools python-wxversion
```


For more info see [http://www.wxpython.org](http://www.wxpython.org)

[SIZE="3"]***Why***[/SIZE]

Unfortunately the latest wxPython packages are not available in the Dapper repositories, but luckily Robin Dunn makes them available through the wxPython repositories. wxPython not only makes [SPE]("http://pythonide.stani.be") possible, but also a lot of other applications such as bittornado.

[SIZE="4"]***Installation***[/SIZE]

You'll need to add some lines to your sources.list. As such you'll always be updated when a new version of wxPython comes out.

> :arrow: If you have the package python wxgtk2.6 already installed you need to uninstall it first:
```
$sudo apt-get remove --purge python-wxgtk2.6 libwxgtk2.6-0
```This might need to uninstall other packages as well. Don't worry! Write them down and install them later back again when you've finished this howto.

```
$sudo gedit /etc/apt/sources.list
```

Paste in these lines.

```
#wxPython official repositories
deb http://starship.python.net/crew/robind/wxPython/apt/ binary/
deb-src http://starship.python.net/crew/robind/wxPython/apt/ source/
```

Now update your Ubuntu system and install wxPython:
```
$sudo apt-get update
$sudo apt-get install python-wxgtk2.6 python-wxtools python-wxversion
```

That's all. You are now ready to install [SPE]("http://pythonide.stani.be").

[SIZE="4"]***Documentation***[/SIZE]

The best starting point is the [wxPython demo]("http://www.wxpython.org/download.php#binaries").
There is a very active and helpfull wxPython community which communicates through the [mailing list]("http://www.wxpython.org/maillist.php").
There are some free video tutorials available at [showmedo.com]("http://showmedo.com/videos/series?name=PythonWxPythonBeginnersSeries").
You can read through the [online wxdocs]("http://www.wxpython.org/onlinedocs.php") or the new [wxPyDocs]("http://www.wxpython.org/docs/api/").
Also check [Andrea Gavana's sexy widgets]("http://xoomer.alice.it/infinity77/eng/freeware.html").

[SIZE="5"]**SPE**[/SIZE]

For more info see [http://pythonide.stani.be](http://pythonide.stani.be)

[SIZE="4"]***Installation***[/SIZE]

Shortly after each release a debian package SPE-wx*.deb will be available on the [SPE website]("http://pythonide.stani.be"). I'd like to thank Marco Ferreira for doing this wonderful job. Also you need to install kiki (regular expression doctor) and wxglade (gui designer). To install simply type in a terminal:
```
$sudo apt-get install kiki python-wxglade
$wget http://download.berlios.de/python/spe_0.8.2a-0ubuntu2_all.deb
$sudo dpkg -i spe_0.8.2a-0ubuntu2_all.deb
```
This will create an entry for [SPE]("http://pythonide.stani.be") in your start Menu under 'Programming'.

[SIZE="4"]***Uninstallation***[/SIZE]

```
$sudo dpkg -r SPE-wx*.deb
```

[SIZE="4"]***Documentation***[/SIZE]

The SPE manual is available at [http://pythonide.stani.be/manual/html/manual.html](http://pythonide.stani.be/manual/html/manual.html) with ads to sponsors SPE development. 

> :KS As an alternative a clean pdf manual ([preview here]("http://pythonide.stani.be/manual/preview.pdf")) which you can print, will be emailed to everyone who [donates]("http://www.stani.be/python/spe/blog/sm_donate") to SPE!!

There are also some free SPE video tutorials available at [showmedo.com]("http://showmedo.com/videos/series?name=PythonDevelopmentWithSPE")

[SIZE="4"]***Help: SPE is looking for MOTU fix***[/SIZE]

Unfortunately the [SPE]("http://pythonide.stani.be") version in the repositories is probably deprecated or broken. I'd wish I had enough time to learn about MOTU and fix this, but unfortunately I don't. Marco did already some great efforts, but appearantly it still needs some help. Any Master of the Universe interested in this? See [https://launchpad.net/distros/ubuntu/+source/spe/0.8.2a-0ubuntu1](https://launchpad.net/distros/ubuntu/+source/spe/0.8.2a-0ubuntu1) It would be nice if [SPE]("http://pythonide.stani.be") is available in the standard Ubuntu repositories.Please contact me if you are interested.

---

### Post by whocarez on 2006-07-19
Hi,

Great tutorial. Just a small note when removing the standard packages from ubuntu repositories:

```
$sudo apt-get remove --purge python-wxgtk2.6
```

I also encountered a conflict when installing the python-wxgtk2.6, it complained about the libwxgtk2.6-0. So I think it's good to remove it too before getting a new one.

```
$sudo apt-get remove libwxgtk2.6-0
```

Before installing SPE from the .deb I had to install kiki and python-wxglade from the ubuntu repositories. Don't know why, but both packages had to be installed at the same time on my system

```
$sudo apt-get install kiki python-wxglade
```

---

### Post by stani on 2006-07-22
Thanks, I ve updated.

---

### Post by Burgresso on 2006-07-24
Awesome! read closer, good tutorial! Don't need to remove anything.

Original post b4 edit:

It's not clear to me: so am supposed to remove anything or not to use just SPE?

gracias,

burgresso

---

### Post by stani on 2006-07-27
Sorry, I don't understand your question. Please reformulate your question.

---

### Post by tseliot on 2006-07-29
I have installed SPE from the repos and it works great. I'm already addicted to it.

Keep up the good work!

---

### Post by LKRaider on 2006-07-29
I believe the new version in the repositiries is fixed now, right? I just installed it, and seems to be working fine :)

(v. 0.8.2a+repack-0.1 )

---

### Post by tseliot on 2006-07-30
I wrote about SPE on my blog:

[http://albertomilone.wordpress.com/2006/07/30/spe-ide-stanis-python-editor/](http://albertomilone.wordpress.com/2006/07/30/spe-ide-stanis-python-editor/)

---

### Post by ember on 2006-08-11
Just one short question - are there plans for localized versions?

---

### Post by stani on 2006-08-23
> Just one short question - are there plans for localized versions?
Not at the moment.

---

### Post by andrewpay on 2006-08-27
The debuger will not work on my system 

I get the following message

RPDB - The Remote Python Debugger, version RPDB_2_0_6,
Copyright (C) 2005 Nir Aides.
Type "help", "copyright", "license" for more information.
*** Password has been set to a random password.
*** Spawning debuggee...
*** Debugee failed to start in a timely manner.


I have seen others with the same problem on ubuntu but have seen no solutions.

---

### Post by Bigglez on 2006-08-27
I like SPE, I used it for a while on Fedora and also on Windows.

Recently I started a project using wxPython and I thought I would try "eric".

Now - this is not about flames! I like SPE! :)

Well, I must say eric is damn fast. It's just .. rapid ... it keeps up with me when I move around.

Now, I don't know if this is just my computer or what, but I am on a 1ghz Athlon AMD with 1gig of RAM and kubu 6.06.

Try this:
1. Open a py file in SPE
2. Open a py file in Eric
3. Scroll up and down by dragging the scrollbar handle.
4. Compare the "smoothness" of the motion.
5. Compare the ease with which you can scroll and slow and stop at a particular line in the code.
6. Do you notice which one "jumps" and "jerks" and "stutters"?

I find GTK based IDE's to be virtually unusable because of this one factor - the slowness of the drawing/updating of the text in the code I am working on. For some reason QT has no such problem - it's as fast as text mode!

If there were a python editor with auto-complete and so forth in pure ncurses - I would be there like flint!

So, I blame GTK, not wxWidgets or wxPython or SPE! Boa-constructor is equally sluggardly. Ugh.

What do you all think?

---

### Post by andrewpay on 2006-08-27
> I find GTK based IDE's to be virtually unusable because of this one factor - the slowness of the drawing/updating of the text in the code I am working on. For some reason QT has no such problem - it's as fast as text mode!

If there were a python editor with auto-complete and so forth in pure ncurses - I would be there like flint!

So, I blame GTK, not wxWidgets or wxPython or SPE! Boa-constructor is equally sluggardly. Ugh.

What do you all think?

Eric uses QT which I believe is liscenced on MS windows:twisted: .  I wish to use cross platform free:KS  software.

---

### Post by Bigglez on 2006-08-27
Yes - there is some Windows licence issue. Not sure.

I find wxPython very nice and quick on Windows - the Windows gui is better than GTK on Linux. Anyways, QT4 will be free on Windows too. Even KDE will be available on Windows! Amazing.

---

### Post by Bigglez on 2006-08-27
But - what about the speed thing? Am I right, or just deluded?

Perhaps there is something I can do to improve the speed of GTK apps. It's one HUGE reason I don't use GNOME...

---

### Post by Bigglez on 2006-08-27
Oh - BTW - the debugger on eric works perfectly too. ;)

---

### Post by stani on 2006-08-27
> RPDB - The Remote Python Debugger, version RPDB_2_0_6,
Copyright (C) 2005 Nir Aides.
Type "help", "copyright", "license" for more information.
*** Password has been set to a random password.
*** Spawning debuggee...
*** Debugee failed to start in a timely manner.

Please go to the winpdb website or contact Nir Aides about this problem. Winpdb has a bug with the default python version of Ubuntu, however it works fine if you try to run it with python 2.3

Stani

---

### Post by Steveire on 2006-09-21
Hi. I recently installed this, and it's impressive. Really good work. There are two or three features I'd really like to see in it though. The top two are features from Kate.

[list]
[*]Highlight the word 'self'. I know it's a convention and not special word in python, but it's handy. 
[*]Close brackets and quotes. When I write 'myFunct(' a ')' is placed after the cursor. Similar for [, {, ", '
[*] Option to use a different interpreter. I use ipython, which has completion features etc. I'd like it built into SPE.
[*]More complicated but also useful would be to automatically add turn 
```

class myClass:<enter>

```
into
```

class myClass:
    def __init__(self, <cursor>):


```
```

class myClass:
    def anyFunction(


```
into
```

class myClass:
    def anyFunction(self, <cursor>):

```
[/list]
Is this stuff possible for me to do with an option I haven't found, or can it be put into a next version? Can it be made easily extensible on the user side?

---

### Post by DC@DR on 2006-09-21
Man, this IDE simply a kick-***! I just love it at the first sight :D ...Keep it up, bro ;)

---

### Post by paul999 on 2006-10-18
Hi 
I've just installed the wxPython as above because I wanted to run Wammu ([http://dl.cihar.com/wammu/latest/wammu-0.15.tar.bz2)](http://dl.cihar.com/wammu/latest/wammu-0.15.tar.bz2)), but on setup of wammu I run into problems:

$ python setup.py build
You need wxPython!
You can get it from <http://www.wxpython.org>

Can anybody tell me what i've done wrong

Thanks

---

### Post by DirtDawg on 2006-10-18
Thanks a ton Stani. SPE is GREAT!

---

### Post by stani on 2006-11-01
> **Steveire said:**
> Hi. I recently installed this, and it's impressive. Really good work. There are two or three features I'd really like to see in it though. The top two are features from Kate.

[list]
[*]Highlight the word 'self'. I know it's a convention and not special word in python, but it's handy. 
[*]Close brackets and quotes. When I write 'myFunct(' a ')' is placed after the cursor. Similar for [, {, ", '
[*] Option to use a different interpreter. I use ipython, which has completion features etc. I'd like it built into SPE.
[*]More complicated but also useful would be to automatically add turn 
```

class myClass:<enter>

```
into
```

class myClass:
    def __init__(self, <cursor>):


```
```

class myClass:
    def anyFunction(


```
into
```

class myClass:
    def anyFunction(self, <cursor>):

```
[/list]
Is this stuff possible for me to do with an option I haven't found, or can it be put into a next version? Can it be made easily extensible on the user side?
Everything is possible, but time is the question. File these as feature requests.If you have some python experience, I could assist you implementing these.

---

### Post by stani on 2007-02-24
The development of SPE is continuing, follow it at:

[http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by devsfan1830 on 2008-04-14
I downloaded and installed SPE to replace IDLE. However when i click the icon to run it shows briefly in the task bar and then doesn't run. I tried reinstalling and nothing, and i have verified i have the most current version of it and its dependent packages. I'm running Ubuntu 7.10.

---

### Post by stani on 2008-04-14
You don't give any information so I can help you (which version did you download? how did you install it?). Anyway as Ubuntu is my main platform, I make sure SPE is available from the repositories. So remove your previous SPE installation and just do:
sudo apt-get install spe

SPE in Hardy will be massively improved later version.

---

### Post by devsfan1830 on 2008-04-14
I installed it via the Synaptic Package manager. I'm not a Linux expert so if you need specific information your going to need to tell me what it is an possibly how to get it. The problem description i gave is as detailed as i can possibly be at this time.

---

### Post by stani on 2008-04-14
> **devsfan1830 said:**
> I installed it via the Synaptic Package manager. I'm not a Linux expert so if you need specific information your going to need to tell me what it is an possibly how to get it. The problem description i gave is as detailed as i can possibly be at this time.
I thought you downloaded it from the spe website. Ok in that case what is the output of:
```
spe --debug
```

---

### Post by sneakers563 on 2008-04-14
I think I'm having the same problem.  It looks like it might be a version incompatibility between spe and wxpython under gutsy.  Incidently, I believe that I have both 2.8.4 and 2.6.3.2.1.5 installed.

This is my output from --debug:

Spe Warning: Spe was developped on wxPython v2.6.1.0., but v2.8.4.0. was found.
If you experience any problems please install wxPython v2.6.1.0.


SPE v0.8.2.a (c)2003-2005 [www.stani.be](www.stani.be)

If spe fails to start:
 - type "python SPE.py --debug > debug.txt 2>&1" at the command prompt
   (or if you use tcsh: "python SPE.py --debug >& debug.txt")
 - send debug.txt with some info to spe.stani.be[at]gmail.com

Blender support disabled (run SPE inside Blender to enable).

Encrypted debugging disabled.
  If you prefer encrypted debugging, install the "Python Cryptography Toolkit"
  from [http://www.amk.ca/python/code/crypto](http://www.amk.ca/python/code/crypto)

Spe is running in debugging mode with this configuration:
- platform  : linux2
- python    : 2.5.1
- wxPython  : 2.8.4.0.
- interface : <default>
- encoding  : UTF-8

Launching application...
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Create: Framework: menu.
Create: Framework: toolbar.
Create: Framework: statusbar.
Traceback (most recent call last):
  File "/usr/bin/spe", line 3, in <module>
    import _spe.SPE
  File "/usr/lib/python2.5/site-packages/_spe/SPE.py", line 209, in <module>
    style           = style)
  File "/usr/lib/python2.5/site-packages/_spe/sm/wxp/smdi.py", line 1278, in __init__
    wx.App.__init__(self,redirect=not debug)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7757, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7354, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/_spe/sm/wxp/smdi.py", line 1298, in OnInit
    **self.attributes)
  File "/usr/lib/python2.5/site-packages/_spe/sm/wxp/smdi.py", line 801, in __init__
    Parent.__init__(self,app=app,page=page,**options)
  File "/usr/lib/python2.5/site-packages/_spe/sm/wxp/smdi.py", line 596, in __init__
    **options)
  File "/usr/lib/python2.5/site-packages/_spe/sm/wxp/smdi.py", line 325, in __init__
    self.__statusBar__()
  File "/usr/lib/python2.5/site-packages/_spe/sm/wxp/smdi.py", line 417, in __statusBar__
    self.statusBar = self.app.StatusBar(parent=self,id=wx.ID_ANY)
  File "/usr/lib/python2.5/site-packages/_spe/Menu.py", line 727, in __init__
    self.throbber   = Throbber(self,'throbber_still.gif')
  File "/usr/lib/python2.5/site-packages/_spe/Menu.py", line 733, in __init__
    GIFAnimationCtrl.__init__(self,statusBar,-1,info.imageFile(fileName))
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/animate.py", line 242, in __init__
    self.LoadFile(filename)
  File "/usr/lib/python2.5/site-packages/_spe/Menu.py", line 746, in LoadFile
    if fileName != self._fileName and not self._running:
AttributeError: 'Throbber' object has no attribute '_fileName'

---

### Post by stani on 2008-04-14
It looks like you need the enable the backport repositories. You can do this in System>Administration>Software Sources

Afterwards you need to update your system with:
```
sudo apt-get update
sudo apt-get python-wxgtk2.6
sudo apt-get dist-upgrade
```

In Hardy all this kind of installation issues will be gone.

---

### Post by sneakers563 on 2008-04-14
> In Hardy all this kind of installation issues will be gone.

I'll just wait for Hardy then.  Thanks for the reply.  SPE is a truly great program.

---

### Post by 24*7 on 2009-04-05
> **stani said:**
> [URL="http://pythonide.stani.be/screenshots/spe-ubu-dapper"][IMG]http://pythonide.stani.be/screenshots/tmb-ubu-dapper[/IMG]
Click for bigger screenshot[/URL]

[More screenshots here...]("http://pythonide.stani.be/screenshots")

The following thread is obsolete. To install SPE just do:

```
sudo apt-get install python-wxversion spe
```

The following thread remains for archiving purposes only.

[SIZE="5"]**Introduction**[/SIZE]

wxPython is a free GUI toolkit for the Python programming language. It allows Python programmers to create programs with a robust, highly functional graphical user interface, simply and easily. On Ubuntu it uses GTK. I'd like to thank Robin Dunn, the author of wxPython, to make this all possible. 

I've written [SPE]("http://pythonide.stani.be"), a python IDE with auto-indentation, auto completion, call tips, syntax coloring, UML viewer, syntax highlighting, class explorer, source index, auto todo list, sticky notes, integrated pycrust shell, python file browser, recent file browser, drag&drop, context help, ... A special feature is [SPE]("http://pythonide.stani.be")'s ability to run interactively inside blender with a 3d object browser.
[SPE]("http://pythonide.stani.be") integrates with XRCed (GUI designer) and ships with wxGlade (GUI designer), PyChecker (source code doctor), Kiki (regular expression console) and WinPdb (remote, multi-threaded debugger). [SPE]("http://pythonide.stani.be") runs on Windows, Linux and Mac OS X.

First make sure you have the pythonX.X-dev package installed. In case you don't have do this in the terminal:
```
$sudo apt-get install python2.4-dev
```

[SIZE="5"]**wxPython**[/SIZE]



For more info see [http://www.wxpython.org](http://www.wxpython.org)

[SIZE="3"]***Why***[/SIZE]

Unfortunately the latest wxPython packages are not available in the Dapper repositories, but luckily Robin Dunn makes them available through the wxPython repositories. wxPython not only makes [SPE]("http://pythonide.stani.be") possible, but also a lot of other applications such as bittornado.

[SIZE="4"]***Installation***[/SIZE]

You'll need to add some lines to your sources.list. As such you'll always be updated when a new version of wxPython comes out.



```
$sudo gedit /etc/apt/sources.list
```

Paste in these lines.

```
#wxPython official repositories
deb http://starship.python.net/crew/robind/wxPython/apt/ binary/
deb-src http://starship.python.net/crew/robind/wxPython/apt/ source/
```

Now update your Ubuntu system and install wxPython:
```
$sudo apt-get update
$sudo apt-get install python-wxgtk2.6 python-wxtools python-wxversion
```

That's all. You are now ready to install [SPE]("http://pythonide.stani.be").

[SIZE="4"]***Documentation***[/SIZE]

The best starting point is the [wxPython demo]("http://www.wxpython.org/download.php#binaries").
There is a very active and helpfull wxPython community which communicates through the [mailing list]("http://www.wxpython.org/maillist.php").
There are some free video tutorials available at [showmedo.com]("http://showmedo.com/videos/series?name=PythonWxPythonBeginnersSeries").
You can read through the [online wxdocs]("http://www.wxpython.org/onlinedocs.php") or the new [wxPyDocs]("http://www.wxpython.org/docs/api/").
Also check [Andrea Gavana's sexy widgets]("http://xoomer.alice.it/infinity77/eng/freeware.html").

[SIZE="5"]**SPE**[/SIZE]

For more info see [http://pythonide.stani.be](http://pythonide.stani.be)

[SIZE="4"]***Installation***[/SIZE]

Shortly after each release a debian package SPE-wx*.deb will be available on the [SPE website]("http://pythonide.stani.be"). I'd like to thank Marco Ferreira for doing this wonderful job. Also you need to install kiki (regular expression doctor) and wxglade (gui designer). To install simply type in a terminal:
```
$sudo apt-get install kiki python-wxglade
$wget http://download.berlios.de/python/spe_0.8.2a-0ubuntu2_all.deb
$sudo dpkg -i spe_0.8.2a-0ubuntu2_all.deb
```
This will create an entry for [SPE]("http://pythonide.stani.be") in your start Menu under 'Programming'.

[SIZE="4"]***Uninstallation***[/SIZE]

```
$sudo dpkg -r SPE-wx*.deb
```

[SIZE="4"]***Documentation***[/SIZE]

The SPE manual is available at [http://pythonide.stani.be/manual/html/manual.html](http://pythonide.stani.be/manual/html/manual.html) with ads to sponsors SPE development. 



There are also some free SPE video tutorials available at [showmedo.com]("http://showmedo.com/videos/series?name=PythonDevelopmentWithSPE")

[SIZE="4"]***Help: SPE is looking for MOTU fix***[/SIZE]

Unfortunately the [SPE]("http://pythonide.stani.be") version in the repositories is probably deprecated or broken. I'd wish I had enough time to learn about MOTU and fix this, but unfortunately I don't. Marco did already some great efforts, but appearantly it still needs some help. Any Master of the Universe interested in this? See [https://launchpad.net/distros/ubuntu/+source/spe/0.8.2a-0ubuntu1](https://launchpad.net/distros/ubuntu/+source/spe/0.8.2a-0ubuntu1) It would be nice if [SPE]("http://pythonide.stani.be") is available in the standard Ubuntu repositories.Please contact me if you are interested.
Most of ur blog has broken links. Even the screenshots posted by you don't work!!!!

---

### Post by DirtDawg on 2009-04-06
> **24*7 said:**
> Most of ur blog has broken links. Even the screenshots posted by you don't work!!!!

That's because the tutorial is for SPE 8.2 while the version in the repository is 8.4, so you're better off using that one.
```
 sudo apt-get install spe 
```

---

