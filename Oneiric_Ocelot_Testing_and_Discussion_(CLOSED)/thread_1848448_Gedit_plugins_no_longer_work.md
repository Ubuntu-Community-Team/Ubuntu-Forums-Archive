---
title: "Gedit plugins no longer work"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mgawin on 2011-09-22
After today updates, some gedit plugins stopped working. 
Anyone knows why?

---

### Post by DavePlummer on 2011-09-24
I dons't know why, but I observed the same problem today.

---

### Post by cariboo on 2011-09-24
Have either of you created a bug report? If so can you post the bug number. If not, why not, if the developers don't know about a problem, they can't fix it.

---

### Post by riftt on 2011-09-24
I searched earlier in the day and I saw this bug reported: [https://bugs.launchpad.net/ubuntu/+source/libpeas/+bug/857348](https://bugs.launchpad.net/ubuntu/+source/libpeas/+bug/857348)

---

### Post by waspbr on 2011-09-24
The bug report proposes launching gedit with 

```
LD_PRELOAD=/usr/lib/libpython2.7.so.1
```

unfortunately that doesn't seem to work for me.

---

### Post by repkam09 on 2011-09-25
I just noticed this issue as well and upon looking for a solution found this thread.

This is the output I get upon trying to enable a plugin:

```
(gedit:16427): libpeas-WARNING **: Error initializing Python Plugin Loader:PyGObject initialization failed
ImportError: could not import gobject (error was: '/usr/lib/libpyglib-gi-2.0-python2.7.so.0: undefined symbol: _Py_ZeroStruct')
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 59, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 16, in <module>
    from xml.parsers.expat import ExpatError
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.so: undefined symbol: _Py_ZeroStruct

Original exception was:
ImportError: could not import gobject (error was: '/usr/lib/libpyglib-gi-2.0-python2.7.so.0: undefined symbol: _Py_ZeroStruct')

(gedit:16427): libpeas-WARNING **: Please check the installation of all the Python related packages required by libpeas and try again

(gedit:16427): libpeas-WARNING **: Loader 'python' is not a valid PeasPluginLoader instance

(gedit:16427): libpeas-WARNING **: Could not find loader 'python' for plugin 'terminal'
```



> **waspbr said:**
> The bug report proposes launching gedit with 

```
LD_PRELOAD=/usr/lib/libpython2.7.so.1
```

unfortunately that doesn't seem to work for me.

Likewise, how would I go about doing this? If I simply do "gedit LD_PRELOAD=/usr/lib/libpython2.7.so.1" I create a text file by that name. (Not surprisingly.)

---

### Post by cariboo on 2011-09-25
Has anyone tried the solution offered in post [#11]("https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/857348/comments/11")?

---

### Post by cariboo on 2011-09-25
Has anyone tried the solution offered in post [#11]("https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/857348/comments/11"), of the bug report?

---

### Post by repkam09 on 2011-09-26
The solution in [Comment #11]("https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/857348/comments/11") did not work for me. The packages linked there are the i386 ones and I was unable to find an amd64 version of that exact version given to try that instead.

Exact error:
```
dpkg: error processing libpeas-1.0-0_1.1.3-0ubuntu1_i386.deb (--install):
 libpeas-1.0-0:i386 1.1.3-0ubuntu1 (Multi-Arch: no) is not co-installable with libpeas-1.0-0:amd64 1.1.4-0ubuntu1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 libpeas-1.0-0_1.1.3-0ubuntu1_i386.deb
```

---

### Post by effenberg0x0 on 2011-09-26
The workaround at Launchpad bug post #11 of [https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/857348/comments/11](https://bugs.launchpad.net/ubuntu/+source/pygobject/+bug/857348/comments/11) only works for me if, after running those commands, I launch Gedit using the following command line:
```

$ DISPLAY=:0.0 PYTHON=/usr/bin/python3.2 LD_PRELOAD=/usr/lib/libpython2.7.so.1 /usr/bin/gedit

```
Of course, if you export those vars, it will run OK. Using env | grep -i ld_preload, env | grep -i python showed I didn't had these env vars.

I am running on 64-bit Oneiric but used the suggested 32-bit packages anyway.

Thanks,
Effenberg

**EDIT:**
Just tested on a fresh Beta 2 VM + apt-get update && sudo apt-get upgrade: The mentioned workaround will really only work when using the command line I suggested in this post.

---

### Post by mc4man on 2011-09-26
If downgrading as a workaround till fixed I'd be inclined to do all the related packages of those 2 sources that are installed (may not be nessasary but personally prefer.
For Ex. **here**

gir1.2-peas-1.0_1.1.3-0ubuntu1_i386.deb 
libpeas-1.0-0_1.1.3-0ubuntu1_i386.deb
libpeas-common_1.1.3-0ubuntu1_all.deb  
python-gobject_2.90.3-1svn1_i386.deb
python-gobject-cairo_2.90.3-1svn1_i386.deb

Then you need to do a restart

---

