---
title: "Building Gimme (panel replacement)"
date: 2006-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by z0r on 2006-08-07
[Gimme]("http://beatnik.infogami.com/Gimmie") is an experimental replacement for the GNOME panel. To use it in Dapper Drake, you'll need the following dependencies:
[LIST]
[*]build-essential
[*]python-dev
[*]python-gtk2-dev
[*]python-gnome2-dev
[*]python-gnome2-desktop
[*]python-gnome2-extras-dev
[*]libgnome-desktop-dev
[*]libgnomecups1.0-dev
[*]libwnck-dev
[/LIST]

Use apt-get or synaptic to install those. Then:
[LIST=1]
[*]Grab the source tarball from [http://beatnik.infogami.com/Gimmie]("http://beatnik.infogami.com/Gimmie"). [*]Unpack it.
[*]Change to the new directory.
[*]Run (in a terminal) ```
./configure && make
```
[/LIST]

Gimmie can then be started by changing to that directory and running ```
./gimmie.py
```

---

### Post by Fab on 2006-08-08
its really nice, one thing that bugs me though is the lack of configuration (any manual way to change that? gconf doesnt have any entries related to it, and there seems to be no config file). also, the clock is cut off for me. other than that, it really saves quite some screen estate. if I could make it a little bit smaller (in height) and autostretch to max. width, it would be perfect :)

---

### Post by z0r on 2006-08-10
I haven't found any way to configure it either. I guess that will come in a later version. I'd really like to make it thinner! Maybe I should just hack it :)

---

### Post by Fab on 2006-08-10
thats a pity :/
```
 /opt/gimmie-0.1.1/gimmie.py
GTK Accessibility Module initialized
there was an error reading the file
Bonobo accessibility support initialized

```
the second line was I hoped a hint for a config file somewhere.. if you find anything in the source on how to change the height or width, please tell me ;)

---

### Post by sethmahoney on 2006-08-25
Has anyone run into the following error when trying to run make (and know what to do about it)?

```

/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive

```

---

### Post by Toxicity999 on 2006-08-26
did you install libxrender-dev? There are alot of sub dependancies to what is listed as well.

---

### Post by Toxicity999 on 2006-08-26
I'd like to add libxml-parser-perl and libglitz1-dev to that req list. This isn't a completely clean environment or anything but I haven't compiled much on this install so probably you guys just already had them by chance.

Edit: In toying with it for a moment it has REAL promise. For anyone not willing to test this it really covers all the basic applet features the gnome panel uses and even can list specific things in categories such as Gaim convos... though it didn't seem to like the newer gaim beta.

---

### Post by stalefries on 2006-08-26
Thank you so much! I had been wanting to do this, but couldn't figure out the dependencies!

---

### Post by sethmahoney on 2006-08-27
> **Toxicity999 said:**
> did you install libxrender-dev? There are alot of sub dependancies to what is listed as well.

Thanks for the tip, but it looks like I've got all three of those dependencies taken care of.  Have you uncovered any more?

---

### Post by sethmahoney on 2006-08-27
Found this for the libXrender problem, which worked: [http://www.ubuntuforums.org/showthread.php?t=238449](http://www.ubuntuforums.org/showthread.php?t=238449)

Only now it seems like its not wanting to find Python.h (or, at least, that's what I assume is causing all the other issues):

```

/usr/include/pygtk-2.0/pygobject.h:5:20: Python.h: No such file or directory
In file included from _gdmclientmodule.c:6:
/usr/include/pygtk-2.0/pygobject.h:20: error: syntax error before "PyObject"
/usr/include/pygtk-2.0/pygobject.h:20: warning: no semicolon at end of struct or union
/usr/include/pygtk-2.0/pygobject.h:21: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:22: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:22: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:24: error: syntax error before '}' token
/usr/include/pygtk-2.0/pygobject.h:27: error: syntax error before "PyObject_HEAD"
/usr/include/pygtk-2.0/pygobject.h:27: warning: no semicolon at end of struct or union
/usr/include/pygtk-2.0/pygobject.h:29: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:30: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:30: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:32: error: syntax error before '}' token
/usr/include/pygtk-2.0/pygobject.h:32: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:38: error: syntax error before "PyObject_HEAD"
/usr/include/pygtk-2.0/pygobject.h:38: warning: no semicolon at end of struct or union
/usr/include/pygtk-2.0/pygobject.h:42: error: syntax error before '}' token
/usr/include/pygtk-2.0/pygobject.h:42: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:48: error: syntax error before "PyObject_HEAD"
/usr/include/pygtk-2.0/pygobject.h:48: warning: no semicolon at end of struct or union
/usr/include/pygtk-2.0/pygobject.h:51: error: syntax error before '}' token
/usr/include/pygtk-2.0/pygobject.h:51: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:60: error: syntax error before "PyObject_HEAD"
/usr/include/pygtk-2.0/pygobject.h:60: warning: no semicolon at end of struct or union
/usr/include/pygtk-2.0/pygobject.h:62: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:67: error: syntax error before "PyTypeObject"
/usr/include/pygtk-2.0/pygobject.h:74: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:76: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:79: error: syntax error before "PyTypeObject"
/usr/include/pygtk-2.0/pygobject.h:79: warning: no semicolon at end of struct or union
/usr/include/pygtk-2.0/pygobject.h:80: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:82: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:84: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:87: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:88: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:88: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:90: error: syntax error before "PyObject"
/usr/include/pygtk-2.0/pygobject.h:91: error: syntax error before "PyObject"
/usr/include/pygtk-2.0/pygobject.h:93: error: syntax error before "PyObject"
/usr/include/pygtk-2.0/pygobject.h:93: error: `register_gtype_custom' declared as function returning a function
/usr/include/pygtk-2.0/pygobject.h:94: error: syntax error before "int"
/usr/include/pygtk-2.0/pygobject.h:95: error: syntax error before "PyObject"
/usr/include/pygtk-2.0/pygobject.h:96: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:96: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:98: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:101: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:101: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:102: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:104: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:105: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:107: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:107: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:108: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:110: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:110: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:112: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:114: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:128: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:128: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:129: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:129: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:130: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:131: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:137: error: syntax error before "PyObject"
/usr/include/pygtk-2.0/pygobject.h:138: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:140: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:142: error: syntax error before "PyObject"
/usr/include/pygtk-2.0/pygobject.h:144: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:144: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:145: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:145: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:148: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:149: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:149: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:151: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:151: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:152: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:152: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:155: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:156: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:156: warning: data definition has no type or storage class
/usr/include/pygtk-2.0/pygobject.h:168: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:171: error: syntax error before '*' token
/usr/include/pygtk-2.0/pygobject.h:175: error: syntax error before '}' token
_gdmclientmodule.c:8: error: syntax error before '*' token
_gdmclientmodule.c:9: error: syntax error before '*' token
_gdmclientmodule.c:10: error: syntax error before "py_gdmclient_functions"
_gdmclientmodule.c:10: warning: data definition has no type or storage class
_gdmclientmodule.c:13: error: syntax error before "init_gdmclient"
_gdmclientmodule.c: In function `init_gdmclient':
_gdmclientmodule.c:15: error: `PyObject' undeclared (first use in this function)
_gdmclientmodule.c:15: error: (Each undeclared identifier is reported only once
_gdmclientmodule.c:15: error: for each function it appears in.)
_gdmclientmodule.c:15: error: `m' undeclared (first use in this function)
_gdmclientmodule.c:15: error: `d' undeclared (first use in this function)
_gdmclientmodule.c:17: error: `gobject' undeclared (first use in this function)
_gdmclientmodule.c:17: error: `mdict' undeclared (first use in this function)
_gdmclientmodule.c:17: error: `cobject' undeclared (first use in this function)
_gdmclientmodule.c:17: error: `PyExc_RuntimeError' undeclared (first use in this function)
_gdmclientmodule.c:17: error: `PyExc_ImportError' undeclared (first use in this function)
_gdmclientmodule.c: At top level:
_gdmclientmodule.c:10: warning: array 'py_gdmclient_functions' assumed to have one element

```

---

### Post by sethmahoney on 2006-08-27
Update: Couldn't get 0.1.1 to work but CVS is working okay!  Unfortunately, the CVS version is kind of ugly and the system tray doesn't work.  : /

---

### Post by Toxicity999 on 2006-08-28
My little review:
I used it for a few minutes and as I said It has potential... A few things scream to me, a configureation panel... perhaps more orientations for the containers.. right now it reminds me too much of that Stardock product made to mimic the OS X Dock for windows (you know the newer version.) The colors are a little... out there... As I said this high efficiency model could be great and would infact be better than the OS X dock but the overhead buttons and just the stillness of the unit seems off. I know the buttons need to be there to access the more advanced menus but ehhhh.... too bulky in it's current form. Now also... it doesn't seem to support dbus calls for Gaim 2.0 contacts... though I didn't test it for 1.5 if course this is easily fixed by prying open the source for the gaim container if you know the calls gaim 2 uses. The entire point of this not eating up the whole screen width is to avoid being out of the way... but the way it's rendered on screen stops windows from maximizing under it which in effect leaves you in the same boat as if your bottom panel were like 50 pixels tall. and  you get that wasted space on the bottom corners there... which really gets to me for some reason. Of course this is very young software and suprisingly stable for its status! All in all once it's fully functional... I'll use it in place of gnome-panel.

---

### Post by sethmahoney on 2006-08-29
Yeah, I agree.  I'm definitely going to keep my eye on this project.

---

### Post by bullon on 2006-08-29
this is great!! on ething though, the "people" feature doesn't seem to work too well... i can add users to the panel and it detects my contacts list, but not whether anyone is online or not (ie every contact appears offline all the time).. hope this problem gets fixed soon!:KS

---

### Post by Toxicity999 on 2006-08-29
If I understand you I think it's the same for me the advanced large menu detects people being on or off just fine. But, when it comes to the actual Panel container it doesn't show a thing. So... maybe it can read from Gaim 2 fine it's just not drawing the updates to the container for some reason. I forgot that bit when I talked about it earlier.

---

### Post by bullon on 2006-09-03
in my case it doesn't even detect people being online or offline, it only shows "recent people" and "everybody". I can place contacts on the panel by right clicking on them and selecting "keep around" but they never appear online, even when they really are...

is there something i need to configure? ](*,)

---

### Post by stalefries on 2006-09-03
By the way, you misspelled "Gimmie" in the title. Otherwise, great HOW-TO.

---

### Post by stalefries on 2006-09-04
By the way, for those of you who are having trouble getting Gaim integration, I installed the Gaim 2.0.0 Beta 3.1 by following the directions in [this post]("http://ubuntuforums.org/showpost.php?p=1456453&postcount=8"), and it works now.

---

### Post by bullon on 2006-09-08
still no luck, i wrote to the gimmie developers, and they told me i need to have the DBUS plugin turned on, i have no idea how to do this... or where to get the dbus plugin,anyone know?

---

### Post by stalefries on 2006-09-08
The DBUS plugin is there, but i think only for the 2.0.0 Beta versions. Go to Tools>Plugins, and enable the DBUS plugin.

---

### Post by bullon on 2006-09-08
for some reason i had to re-install gaim (was already running beta 2.00) but now its working well thanks!! it only shows contacts i chose to "keep around" though, not anyone i may be chatting with...

---

