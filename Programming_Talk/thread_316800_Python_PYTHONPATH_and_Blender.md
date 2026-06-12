---
title: "Python PYTHONPATH and Blender"
date: 2006-12-11
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2006-12-11
Hello, I wanted to post this in programming talk to get input from any python coders. I have the AMD 64. Any software that installs in 64-bit is amazing. I have tried building software without much luck. To do a linux build requries downloading a whole bunch of libraries.

Blender (3-D authoring program) did install from Synaptic. However, Blender relies on python for many of the modules. I found the wiki for Blender and their python scripts.

[COLOR="Red"]*They say:*[/COLOR]

user@user-desktop:~$ python

[COLOR="Red"]*I get*[/COLOR]
Python 2.4.3 (#2, Oct  6 2006, 07:49:22)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

[COLOR="Red"]*and then*[/COLOR]
>>> import sys
>>> print sys.path
['', '/usr/lib/python24.zip', '/usr/lib/python2.4', '/usr/lib/python2.4/plat-linux2', '/usr/lib/python2.4/lib-tk', '/usr/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages/HTMLgen', '/usr/lib/python2.4/site-packages/Numeric', '/usr/lib/python2.4/site-packages/PIL', '/usr/lib/python2.4/site-packages/cairo', '/usr/lib/python2.4/site-packages/gst-0.10', '/usr/lib/python2.4/site-packages/gtk-2.0']

they say: [COLOR="Red"]*Add this to your favourite rc file as an environment variable setting. For example, add in your .bashrc the line*[/COLOR]

```
export PYTHONPATH=/usr/local/lib/python2.2:/usr/local/lib/python2.2/plat-linux2:/usr/local/lib/python2.2/lib-tk:/usr/local/lib/python2.2/lib-dynload:/usr/local/lib/python2.0/site-packages


```

:confused: Can anyone tell me what my PYTHONPATH should be??? I am hesitant to add to .bashrc because the jave_home variable has been particulary elusive on 64-bit ubuntu. The reason is java is two-thirds 32-bit and the ubuntu workarounds have me with 3 java folders. When I added **export PATH=JAVA_HOME ... **to .bashrc I could not reboot. I had to Nano to the file and delete my java path info.

Thanks in advance. Python and/or Ruby are things I want to learn, but right now I'm involved with java3d and making it interactive.

---

### Post by Unterseeboot_234 on 2006-12-11
Hey, buried deep, deep in the online help was one mention about python and blender. IF you start Blender with the menu, there is no python "console". If, however, you start Blender from Terminal, i.e. user@user:~$ you get the python engine.

Then you have Blender like you normally expect it as a workspace and a terminal window. Now, when I tried to import a mesh model, which is behind-the-scenes python script fired by the menu, I get
```
Using Python version 2.4
Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
```

Any ideas on how to set this variable? I DO jave libtiff.

Thanks, any ideas at all. I don't know python. I know setenv is not on the ubuntu for things like doing java's javac from terminal.

---

### Post by Wybiral on 2006-12-11
What exactly are you asking? I have blender installed (from synaptic) and everything is fine. I can even write python scripts for automating things in blender. What do you need the "PYTHONPATH" for?

---

### Post by Unterseeboot_234 on 2006-12-11
I tried to use import for a 3ds.
IF I started Blender (64-bit ubuntu and 64-bit Blender) from a terminal, I get

"Import failed. Could not load libtiff"

Should I symlink libtiff in usr/share

The PYTHONPATH was 2.31 onoline docs. I won't do that.

user@user-desktop:~$ blender
Using Python version 2.4
Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
--------------------------------
Importing "/home/user/blackhawk.3ds"
Traceback (most recent call last):
  File "<string>", line 646, in my_callback
  File "<string>", line 634, in load_3ds
  File "<string>", line 603, in process_main_chunk
  File "<string>", line 260, in process_object_block
  File "<string>", line 199, in getUniqueName
ValueError: object "fin" not found

---

### Post by Unterseeboot_234 on 2006-12-12
Okay, close this one. Repositories have Blender 2.41, web site to Blender says 2.42 fixes known Python issues. I suspect glib, or something like that, has the wrappers to get to libtiff and connect it to Blender. /usr/lib/libtiff.so.4 doesn't fix this little feature: to use .tif graphic format for Blender. 

Odd, that Gimp, OpenOffice and Wings3D have no problems with tiff files and Wings3D is the workaround to import .3ds models that have .tif textures already on them.

---

### Post by moon_goose on 2009-06-21
> **Unterseeboot_234 said:**
> Hey, buried deep, deep in the online help was one mention about python and blender. IF you start Blender with the menu, there is no python "console". If, however, you start Blender from Terminal, i.e. user@user:~$ you get the python engine.



Thank you for the tip. I almost cracked my head open trying to figure whereabouts of this cosole

---

