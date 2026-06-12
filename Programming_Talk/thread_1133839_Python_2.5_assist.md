---
title: "Python 2.5 assist"
date: 2009-04-23
forum: Programming Talk
---

### Post by David C. on 2009-04-23
Learning python here...in the IDLE I entered help() then enter modules to see what modules were available & received this traceback error.
```
Traceback (most recent call last):
  File "<pyshell#6>", line 1, in <module>
    help()
  File "/usr/lib/python2.5/site.py", line 342, in __call__
    return pydoc.help(*args, **kwds)
  File "/usr/lib/python2.5/pydoc.py", line 1649, in __call__
    self.interact()
  File "/usr/lib/python2.5/pydoc.py", line 1667, in interact
    self.help(request)
  File "/usr/lib/python2.5/pydoc.py", line 1683, in help
    elif request == 'modules': self.listmodules()
  File "/usr/lib/python2.5/pydoc.py", line 1804, in listmodules
    ModuleScanner().run(callback)
  File "/usr/lib/python2.5/pydoc.py", line 1855, in run
    for importer, modname, ispkg in pkgutil.walk_packages():
  File "/usr/lib/python2.5/pkgutil.py", line 110, in walk_packages
    __import__(name)
  File "/usr/lib/python2.5/site-packages/uniconvertor/__init__.py", line 54, in <module>
    sys.exit(1)
SystemExit: 1
```

I ran keywords and got them, ran topics and few of the topics and received the definitions. But wasn't able to get a list of modules. I double checked Synaptic uninstalled and reinstalled Python and its associated libs. Reinstalled the IDLE (both of the available ones for 2.5.2, one is listed as a default). Still getting the above error. 

Also, where is the documentation stored? And how do I access it? I installed it, can't find it or the book Dive Into Python that is listed in the PM, which is installed. Installed C++ Annotations a pdf file (also listed in the PM) to see if it showed up, couldn't find that anywhere upon running a search through the entire file system or any docs related to Python 2.5.  I'm still getting accustomed w/Ubuntu & Linux so bear with me here, please, as I'm not familiar with the os set up moved from Windows XP over this passed weekend (ugh).

---

### Post by David C. on 2009-04-23
Addendum to the above...I went back and opened the pydoc.py file & read through some of the line code listed in the error. However, I don't understand it all. I haven't got that far along in my learning to debug it correctly.

```
def __call__(self, request=None):
        if request is not None:
            self.help(request)
        else:
            self.intro()
          [COLOR="Red"]  self.interact()[/COLOR]
            self.output.write('''
You are now leaving help and returning to the Python interpreter.
If you want to ask for help on a particular object directly from the
interpreter, you can type "help(object)".  Executing "help('string')"
has the same effect as typing a particular string at the help> prompt.
''')

    def interact(self):
        self.output.write('\n')
        while True:
            try:
                request = self.getline('help> ')
                if not request: break
            except (KeyboardInterrupt, EOFError):
                break
            request = strip(replace(request, '"', '', "'", ''))
            if lower(request) in ('q', 'quit'): break
            [COLOR="Red"]self.help(request)[/COLOR]
```

Lines 1649 & 1667 are in red. While I recognize some of the syntax, I don't understand how these errors, and the remaining errors, occurred & would like to know how to go about correcting them. Any assistance is appreciate. Thanks.

---

### Post by Kilon on 2009-04-23
it is extremely strange that you have issues with the help() functions. 

I have even typed "modules" in my ipod touch and my palm treo 750 phone and still it can find all modules. 

Maybe the paths are not set correctly. I do not think it is a code problem. Even though I find it strange that reports an error. 

Have you installed python through synaptic ?

It is normal to take you at least a week getting used to the UBUNTU interface. So hang in there , I am sure you will find it a worthwhile experience and highly rewarding.

you can download or browse online the docs here 

[http://www.python.org/doc/](http://www.python.org/doc/)

---

### Post by David C. on 2009-04-23
Thanks Kilon. 

Yes. I installed it from Synaptic. I thought about installing 3.0 to see if I get the same issue. But I have some concern if both versions will run. I run 2.5 simply because I use Blender 2.48 which will not run off the newer python version. 

I don't understand why it's occurring either. I've uninstalled and reinstalled twice now and keep getting the same error when I enter "modules". Maybe downloading from python and installing maually will alleviate the issue. As for the docs, I have them bookmarked. Thanks again.

---

### Post by elbarto_87 on 2009-04-24
I have also got 8.10 ubuntu installed and noticed a similar problem with idle last night.

```

>>> help('modules')

Please wait a moment while I gather a list of all available modules...

[]
[1, 2]
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    help('modules')
  File "/usr/lib/python2.5/site.py", line 342, in __call__
    return pydoc.help(*args, **kwds)
  File "/usr/lib/python2.5/pydoc.py", line 1646, in __call__
    self.help(request)
  File "/usr/lib/python2.5/pydoc.py", line 1683, in help
    elif request == 'modules': self.listmodules()
  File "/usr/lib/python2.5/pydoc.py", line 1804, in listmodules
    ModuleScanner().run(callback)
  File "/usr/lib/python2.5/pydoc.py", line 1855, in run
    for importer, modname, ispkg in pkgutil.walk_packages():
  File "/usr/lib/python2.5/pkgutil.py", line 125, in walk_packages
    for item in walk_packages(path, name+'.', onerror):
  File "/usr/lib/python2.5/pkgutil.py", line 110, in walk_packages
    __import__(name)
  File "/usr/lib/python2.5/site-packages/matplotlib/config/__init__.py", line 5, in <module>
    from rcparams import rc
  File "/usr/lib/python2.5/site-packages/matplotlib/config/rcparams.py", line 117, in <module>
    rcParams = rc_params()
  File "/usr/lib/python2.5/site-packages/matplotlib/config/rcparams.py", line 49, in rc_params
    fname = get_config_file()
  File "/usr/lib/python2.5/site-packages/matplotlib/config/cutils.py", line 181, in get_config_file
    path =  get_data_path() # guaranteed to exist or raise
  File "/usr/lib/python2.5/site-packages/matplotlib/config/verbose.py", line 74, in wrapper
    ret = func(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/matplotlib/config/cutils.py", line 129, in _get_data_path_cached
    defaultParams['datapath'][0] = _get_data_path()
  File "/usr/lib/python2.5/site-packages/matplotlib/config/cutils.py", line 125, in _get_data_path
    raise RuntimeError('Could not find the matplotlib data files')
RuntimeError: Could not find the matplotlib data files


```

Not sure what it all means tho.

---

### Post by Kilon on 2009-04-24
it smell like a falty install to me. I had hard time to make 2.6 run on macos for example. So maybe it worth posting the problem in the python mailing list, maybe they screwed up something.

---

### Post by David C. on 2009-04-24
You recieved more errors than I did. Though I noticed you didn't get the error for line 1667. Odd. 

This is weird. I wonder if it has something to do with the way Python installs from the Synaptic. Or, as Kilon suggests, it may be a path issue. But I'm not sure how to check and correct it. If that's the case I would need some guidance. I think I'll download from python's site and do a manual install, but that begs the question - if it's a path issue wouldn't it still exist after a manual install?

EDIT: Kilon, I previously had 2.5 on a XP os and don't recall experiencing this issue. Though I did have some, I was able to pull up the modules from the help prompt.

---

### Post by Kilon on 2009-04-24
```
 but that begs the question - if it's a path issue wouldn't it still exist after a manual install?

```

paths are set by the install , so it makes sense. 

It might be of course something else. By the way synaptic does not update as fast as python website. So generally it is a good ide to download from there. 

Oh and there and you can get 2.6 or 3.0 maybe this way you will solve both of your problems. 

> EDIT: Kilon, I previously had 2.5 on a XP os and don't recall experiencing this issue. Though I did have some, I was able to pull up the modules from the help prompt.

Well it is all part of the game. 2.6 was completely broken in MACOS , Totally screwed install files. But those things are expected. 

I would sya to try all available python version till you find the one that works from you. Download only for the python website and post any bug in the mailing list for extra help.

Do not waste your time with fixing things, they might be already fixed .

---

### Post by David C. on 2009-04-24
Thanks, Kilon. 

3.0 is already in the Synaptic, so I wonder if there's a path issue with that version? I'll download 2.5 from py's site. As I previously mentioned, I use Blender 2.48 and it won't operate with any py version beyond 2.5.2. I believe this is changing w/Blender's 2.5 version, at least I hope so. Thanks again.

---

### Post by Kilon on 2009-04-24
> **David C. said:**
> Thanks, Kilon. 

3.0 is already in the Synaptic, so I wonder if there's a path issue with that version? I'll download 2.5 from py's site. As I previously mentioned, I use Blender 2.48 and it won't operate with any py version beyond 2.5.2. I believe this is changing w/Blender's 2.5 version, at least I hope so. Thanks again.


hey I am a blender user myself. 

Take a  look.  

[http://blenderartists.org/forum/showthread.php?t=148097&page=3](http://blenderartists.org/forum/showthread.php?t=148097&page=3)

---

### Post by David C. on 2009-04-24
Small community, isn't it? Nice dragon. 

Out of curiousity are you running Blender on Ubuntu? If so, how did you adjust your graphics card? Mine is moving *really* slow just attempting to get a mesh extruded is painful. I've enable the graphics card but am having issues trying to get it to work properly. For now, I disable it because of the way everything became so enlarged and when I attempted to adjust the screen resolution it went black and the monitor popped up a box stating no input signal. I ended up having to reinstall the os to fix it because I couldn't see anything.

---

### Post by Kilon on 2009-04-24
> **David C. said:**
>  Small community, isn't it? Nice dragon. 

Out of curiousity are you running Blender on Ubuntu? If so, how did you adjust your graphics card? Mine is moving *really* slow just attempting to get a mesh extruded is painful. I've enable the graphics card but am having issues trying to get it to work properly. For now, I disable it because of the way everything became so enlarged and when I attempted to adjust the screen resolution it went black and the monitor popped up a box stating no input signal. I ended up having to reinstall the os to fix it because I couldn't see anything. 

Thanks. 

How adjust it... well more like a total UBUNTU meltdown. I experienced several crashes and complete meltdown of the instalation because of my graphic card. Drivers is certain UBUNTU's greatest weakness. 

But few minutes ago i installed 9.04 and unlike 8.04 it detected my card immediately and it does not create the same problems.

Well fingers crossed. I am going to try Blender again. Last time was a disaster. 

I use MACOS for all my serious stuff by the way and a iMAC CORE2DUO 2.0 GHZ

---

### Post by Kilon on 2009-04-24
I have very good news....

in 9.04 help() works flawlessly, it uses python 2.6 by the way. 

Blender behaves properly now ( I had problem displaying the render window in 8.04) which means that my graphic driver problem are probably gone . Ubuntu window redraw problems have just disappear , nice....

it seem I am back with Ubuntu. Bye windows. I hope this time my problems will be minimum.

My advice is to go get 9.04. It seems to solves alot of issues.

---

### Post by David C. on 2009-04-24
Geesh...I'm in the process of installing Py 3.0.1 right now, running "make test" and it's like the energizer bunny...going and going and going and going....The Py 3.0 IDLE in Synaptic wouldn't install kept getting an error. 

Downloaded 3.0.1 and followed the install directions I found here: [Compiling and Installing software from source]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html") real easy to follow tutorial. 

I ran Blender after I uninstalled most of 2.5, wouldn't let me do a complete removal due to some dependencies. But Blender still works. 

Test is done, of course there is an issue. Tcl/tk libs and/or headers not found. Instructions state to check "setup.py" under detect_module() to find the bits to build modules not found. There is ten, I'm not listing them. But my question is: Do I run the setup.py file as "make setup.py" to add those bits?

As for 9.04, I'll look into it. Thanks.

---

### Post by Kilon on 2009-04-24
> **David C. said:**
> Geesh...I'm in the process of installing Py 3.0.1 right now, running "make test" and it's like the energizer bunny...going and going and going and going....The Py 3.0 IDLE in Synaptic wouldn't install kept getting an error. 

Downloaded 3.0.1 and followed the install directions I found here: [Compiling and Installing software from source]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html") real easy to follow tutorial. 

I ran Blender after I uninstalled most of 2.5, wouldn't let me do a complete removal due to some dependencies. But Blender still works. 

Test is done, of course there is an issue. Tcl/tk libs and/or headers not found. Instructions state to check "setup.py" under detect_module() to find the bits to build modules not found. There is ten, I'm not listing them. But my question is: Do I run the setup.py file as "make setup.py" to add those bits?

As for 9.04, I'll look into it. Thanks.


If I am not mistake it is actually 

```

Python setup.py install 
```

---

### Post by David C. on 2009-04-24
Thanks. I'll give it a go.

---

