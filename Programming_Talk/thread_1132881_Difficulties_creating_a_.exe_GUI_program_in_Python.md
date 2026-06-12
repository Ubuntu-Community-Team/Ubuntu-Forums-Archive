---
title: "Difficulties creating a .exe GUI program in Python"
date: 2009-04-22
forum: Programming Talk
---

### Post by FalFire on 2009-04-22
Hi,

My objective is very simple: I want to make a GUI application with python + one of the available GUI toolkits for Python. It has to look native in both Linux and Windows, and has to be distributed in the form of an executable application for the windows users. Apparently this is not that easy...

I first made the whole program (not so big but still...) using PyGTK and it worked and looked fantastic under both Ubuntu and Windows. However, when I tried to make an .exe out of it using Py2exe, I found out that in order to be able to run my program you have to install GTK, PyGTK, PyGObject and PyCairo! The target users of my program wouldn't want to install all those dependencies just to use my program. I then tried to bundle all the dependencies with the .exe. It worked, but now my program is about 30mb big and has hundreds of files and a few subdirectories apart from my .exe. Not so ideal either. Bundling it into one .exe would solve my problem, but that just doesn't work.

I then rewrote the whole program, this time using wxPython. It immediately looked worse than PyGTK under Ubuntu, and I quickly ran into a couple of problems: I can't make my application window (which has no border, a custom shape and a background image) and all widgets it contains transparent, and under windows the background of each wx.StaticText widget is greyish. It doesn't look as good as the PyGTK under Windows either, but I can make a single .exe file out of it!

So, I guess I am asking whether anyone knows the solution to my problems of one of the two versions? I either need to find a way to make my PyGTK version (a lot) smaller and without so much files OR into one .exe, or to get the same looks using wxPython and to get the transparency working.

---

### Post by giuspen on 2009-04-23
may i ask u to post the setup.py file u used in py2exe?
in the meanwhile i show u mine (i generate a folder of 9 MB with exe inside, if u want to create the installer watch [http://nsis.sourceforge.net/Main_Page]("http://nsis.sourceforge.net/Main_Page")):

[PHP]# setup.py
from distutils.core import setup
import py2exe
import glob

setup(
   name = "U1 Trace Parser",
   description = "Trace GSM U1 Traces",
   version = "0.1",
   windows = [{"script": "u1-trace-parser.py"}],
   options={"py2exe": {"includes": "pango,cairo,pangocairo,atk,gobject,gtk,pygtk,messages,stealth,stealth_print",
                       "dll_excludes": [ "iconv.dll","intl.dll","libatk-1.0-0.dll",
                                         "libgdk_pixbuf-2.0-0.dll","libgdk-win32-2.0-0.dll",
                                         "libglib-2.0-0.dll","libgmodule-2.0-0.dll",
                                         "libgobject-2.0-0.dll","libgthread-2.0-0.dll",
                                         "libgtk-win32-2.0-0.dll","libpango-1.0-0.dll",
                                         "libpangowin32-1.0-0.dll"]}},
   data_files=[("config.pkl"),("msgcat.pkl"),("glade", glob.glob("glade/*.*"))]
)
[/PHP]

---

### Post by Jacks0n on 2009-04-23
There's a couple of installers for windows, which create .exe files. The most popular's called [[COLOR="Blue"]Py2exe[/COLOR]]("http://www.py2exe.org"), the other I've used is [[COLOR="Blue"]PyInstaller[/COLOR]]("http://www.pyinstaller.org/").

[[COLOR="Blue"]A quick search[/COLOR]]("http://www.py2exe.org/index.cgi/Py2exeAndPyGTK") for GTK, shows that you can actually bundle GTK with your program.

Oh, and after you've made the .exe file, use a program called [UPX]("http://upx.sourceforge.net/"). It'll reduce the executable size considerably (depending on what's in it). Most of my Qt programs are reduced to about 1/4 of their original size after using the tool.

Jackson

---

### Post by FalFire on 2009-04-23
Hi,

You got me one step further! My setup.py was more or less the same as the one you posted except for two things: I didn't exclude those dll's which caused my program to be so big, and I had 'Zipfile: None' in my file, which apparently didn't work.

I used your setup.py and now I also managed to get a dist folder of about 10mb, thanks! Do I still need to bundle the etc, lib and share directories of my GTK install with my program? On my PC it works without doing that but is that because I have GTK already installed? I would also like to get a single .exe by using bundle_files = 1 or 2. Each time I try that I get a bunch of errors. Is this possible?

---

### Post by giuspen on 2009-04-23
> **FalFire said:**
> Hi,

You got me one step further! My setup.py was more or less the same as the one you posted except for two things: I didn't exclude those dll's which caused my program to be so big, and I had 'Zipfile: None' in my file, which apparently didn't work.

I used your setup.py and now I also managed to get a dist folder of about 10mb, thanks! Do I still need to bundle the etc, lib and share directories of my GTK install with my program? On my PC it works without doing that but is that because I have GTK already installed? I would also like to get a single .exe by using bundle_files = 1 or 2. Each time I try that I get a bunch of errors. Is this possible?

No u don't have to bundle anything, all the needed .dll are already into the /dist folder, the result is independent from GTK and python.
About a single .exe I can't help u because I never tried it.
Cheers.

---

### Post by nvteighen on 2009-04-23
In a single word: you want to static link GTK+ and dependencies into your .exe.

Well, I doubt you have another chance that live with that 30mb file... That's one reason why dynamic linking was created :p Probably, if you wrote your application in C and compile it linking GTK+ statically, you'd get a similar result (a bit leighter because you won't be embedding the Python runtime too).

I don't get why is it wrong to have those subfolders... Have you looked at other Windows applications? They usually do that.

---

### Post by FalFire on 2009-04-23
@giuspen:
Hmm can you explain how exactly you accomplished that? I can't get it to work on another computer that doesn't have GTK and python installed without adding the lib, share and etc directories of my GTK install to the dist folder and NOT excluding those dll's in the setup.py file that you posted. Your method does work on my computer though...

@nvteighen
Yes, I guess I want to statically link those files into my .exe, but I can't get it to work, that's the problem! I now have a 30mb folder, not a file.

This is the setup.py file I'm using:
```
from distutils.core import setup
import py2exe

setup(
    name = 'MyProg',
    description = 'MyProg',
    version = '1.0',

    console = [
                  {
                      'script': 'myprog.py',
                  }
              ],

    options = {
                  'py2exe': {
                      'packages':'encodings',
                      'includes': 'cairo, pango, pangocairo, atk, gobject',
                      'dll_excludes': [ "iconv.dll","intl.dll","libatk-1.0-0.dll",
                                         "libgdk_pixbuf-2.0-0.dll","libgdk-win32-2.0-0.dll",
                                         "libglib-2.0-0.dll","libgmodule-2.0-0.dll",
                                         "libgobject-2.0-0.dll","libgthread-2.0-0.dll",
                                         "libgtk-win32-2.0-0.dll","libpango-1.0-0.dll",
                                         "libpangowin32-1.0-0.dll"]
                  }
              },

    data_files=[
                   'images/img1.png',
                   'images/img2.png'
               ]
)
```

---

### Post by giuspen on 2009-04-24
> @giuspen:
Hmm can you explain how exactly you accomplished that? I can't get it to work on another computer that doesn't have GTK and python installed without adding the lib, share and etc directories of my GTK install to the dist folder and NOT excluding those dll's in the setup.py file that you posted. Your method does work on my computer though...
Strange because I'm the only one in my office that has python and GTK installed but everybody can use my application.

A tip: to the bottom of [http://www.py2exe.org/index.cgi/Tutorial]("http://www.py2exe.org/index.cgi/Tutorial") u can read:> If the program works on your computer, but not on the user's computer, they may have to install the Microsoft Visual C++ 2008 redistributable package, which can be found on Microsoft's website. This typically occurs when the user does not have python installed. 
Cheers.

---

