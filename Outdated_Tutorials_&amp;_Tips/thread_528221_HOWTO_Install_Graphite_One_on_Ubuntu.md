---
title: "HOWTO: Install Graphite One on Ubuntu"
date: 2007-08-17
forum: Outdated Tutorials &amp; Tips
---

### Post by xethm55 on 2007-08-17
I have been looking for a good CAD program that I can use in Linux around the house.  GraphiteOne seems to satisfy this niche quite well.  However it was troublesome to install.  I figured that some people might benefit from a How to as most of the information to install on Ubuntu is in French. (Google translation leaves much to be desired)  Below is a compiled information that I found along with my own implementations on how to install GraphiteOne (yes, in English).  

A warning: This process utilizes rpms; install at your own risk.  I am not responsible for any damage caused by this guide.  That being said, I will try to help out as much as I can but I am new to Linux.

Step 1:[INDENT]Download Graphite One libraries and 3D modeling packages from [COLOR=black][http://www.graphiteone-cad.com/en/index.htm](http://www.graphiteone-cad.com/en/index.htm)[/COLOR]. (you can optionally download the KDE integration package if you have Kubuntu installed)
[/INDENT]Step 2:[INDENT]Install alien from the repositories:
```
sudo apt-get install alien
```Select yes when it asks to install all packages
[/INDENT]Step 3:[INDENT]Use alien to convert the rpms into debs:
```
sudo alien -c -d graphiteone-3d-design-1.3-1-free.rpm
``````
sudo alien -c -d graphiteone-libs-1.3-1-suse93.rpm
```Optionally:
```
sudo alien -c -d graphiteone-kde-1.3-1-suse93.rpm
```[/INDENT]Step 4:[INDENT]Install the packages using dpkg in the following order:
```
sudo dpkg -i graphiteone-libs_1.3-2_i386.deb 
``````
sudo dpkg -i graphiteone-3d-design_1.3-2_i386.deb
```Optionally:
```
sudo dpkg -i graphiteone-kde-1.3-2_i386.deb
```[/INDENT]Step 5:[INDENT]You need to change the permissions on the files in the lib directory to be writable. First change directories:
```
cd /opt/GraphiteOne/lib
```then change permissions:
```
sudo chmod +w *
```[/INDENT]Step 6:[INDENT]You need to edit two files to change the encoding. Make the following line:
```
# coding=utf-8
``` the first line of the two files opened with the following commands:
```
sudo gedit graphiteoneutils.py
``````
sudo gedit graphiteonedxfreader.py
```make sure to save the files, then exit gedit.  

[/INDENT]Step 7:[INDENT]Create a launcher for the program that will show up under graphics in the main menu. To do this utilize the following commands:
```
sudo gedit /usr/share/applications/GraphiteOne.desktop
```Once that is open copy the following into the new file:
```
[Desktop Entry]
Version=1.3
Encoding=UTF-8
Type=Application
Name=Graphite One
Comment=Model 3D objects
Exec=bash /opt/GraphiteOne/bin/graphiteone --ogl=yes
Icon=/opt/GraphiteOne/data/hi48-app-graphiteone.png
Categories=Graphics;3DGraphics;CAD;
```Save the file and exit gedit. You should now have a launcher under the Graphics section of the Applications menu.

[/INDENT]You are now done.  Enjoy.

-xethm55

P.S.  This is my first HOWTO any feedback would be appreciated.

Sources:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=989439](http://forum.ubuntu-fr.org/viewtopic.php?pid=989439)
[http://doc.ubuntu-fr.org/graphiteone](http://doc.ubuntu-fr.org/graphiteone)
[http://www.linuxgraphic.org/forums/viewtopic.php?t=2669](http://www.linuxgraphic.org/forums/viewtopic.php?t=2669)

---

### Post by Hayesio on 2007-09-28
Hi xethm55,

I followed your HOWTO but i seem to have an API mismatch.  Here is the terminal output:

```
jack@Star-Ship-Omega:~$ bash /opt/GraphiteOne/bin/graphiteone --ogl=yes
/opt/GraphiteOne/lib/HPY.py:2: RuntimeWarning: Python C API version mismatch for module HPYc: This Python has API version 1013, module HPYc has version 1012.
  import HPYc
/opt/GraphiteOne/lib/qt.py:46: RuntimeWarning: Python C API version mismatch for module libsip: This Python has API version 1013, module libsip has version 1012.
  import libsip
/opt/GraphiteOne/lib/qt.py:46: RuntimeWarning: Python C API version mismatch for module libsip: This Python has API version 1013, module libsip has version 1012.
  import libsip
/opt/GraphiteOne/lib/qt.py:50: RuntimeWarning: Python C API version mismatch for module libqtc: This Python has API version 1013, module libqtc has version 1012.
  import libqtc
/opt/GraphiteOne/lib/qt.py:50: RuntimeWarning: Python C API version mismatch for module libqtc: This Python has API version 1013, module libqtc has version 1012.
  import libqtc
/opt/GraphiteOne/lib/qtxml.py:38: RuntimeWarning: Python C API version mismatch for module libqtxmlc: This Python has API version 1013, module libqtxmlc has version 1012.
  import libqtxmlc
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/opt/GraphiteOne/lib/oc.py:6: RuntimeWarning: Python C API version mismatch for module libocc: This Python has API version 1013, module libocc has version 1012.
  import libocc
GOneStatusBar : running without parametric design extension
GOnePersistentElement : running without parametric design extension
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteone.py", line 15, in <module>
    from graphiteoneapplication import GOneApplication
  File "/opt/GraphiteOne/lib/graphiteoneapplication.py", line 25, in <module>
    from graphiteoneframe import *
  File "/opt/GraphiteOne/lib/graphiteoneframe.py", line 21, in <module>
    from graphiteonemenudata import *
  File "/opt/GraphiteOne/lib/graphiteonemenudata.py", line 15, in <module>
    from graphiteonemenuwidget import *
  File "/opt/GraphiteOne/lib/graphiteonemenuwidget.py", line 16, in <module>
    from graphiteoneparteditor import *
  File "/opt/GraphiteOne/lib/graphiteoneparteditor.py", line 15, in <module>
    from graphiteonepartelement import GOnePartElement
  File "/opt/GraphiteOne/lib/graphiteonepartelement.py", line 22, in <module>
    from graphiteonepartshadowelement import GOnePartShadowElement
  File "/opt/GraphiteOne/lib/graphiteonepartshadowelement.py", line 18, in <module>
    from graphiteonetciohandler import GOneTCIOElementHandler
  File "/opt/GraphiteOne/lib/graphiteonetciohandler.py", line 25, in <module>
    from graphiteoneworkingplane import GOneWorkingPlane
  File "/opt/GraphiteOne/lib/graphiteoneworkingplane.py", line 19, in <module>
    from graphiteoneutils import TC_TrsfToHoopsMatrix
  File "/opt/GraphiteOne/lib/graphiteoneutils.py", line 2
    """
    ^
IndentationError: unexpected indent
jack@Star-Ship-Omega:~$ 


```

Any idea how to fix this?

Thanks

---

### Post by dwende on 2007-10-07
Thanks for the tutorial but I am having similar problems with
some sort of incompatability with python. 

David

---

### Post by vincenzoo on 2007-10-21
i'm having  a problem:

[COLOR="Olive"]vincen-zoo@vincenzoo:/opt/GraphiteOne/lib$[/COLOR] graphiteone --ogl=yes
/usr/bin/graphiteone: 19: function: not found
usage : graphiteone [options]
Options:
   --ogl=[yes|no]               Enable/Disable OpenGL display driver (default is no).
   --fsaa-mode=[0..5]           Enable FSAA mode for nVidia graphic cards (experimental!).
   --python=[python executable] The python executable to use (default is python).
   --paths=[path:...]           More entries for PYTHONPATH.

can i do something?

---

### Post by Slingshot on 2007-11-09
Thanks for the guide **xethm55**. Mine is returning a error regarding the coding

```

SyntaxError: Non-ASCII character '\xf8' in file /opt/GraphiteOne/lib/graphiteoneutils.py on line 802, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

I just inserted the coding line after the import statements, im thinking that may be wrong. Were did you insert this line?



**Hayesio** - Python is picky about indenting

```

File "/opt/GraphiteOne/lib/graphiteoneutils.py", line 2
    """
    ^
IndentationError: unexpected indent

```

Open that file and check there is no indents.

Thanks
SlingShot

---

### Post by xethm55 on 2007-11-12
First of all I would like to appologize about taking so long.  

Hayesio: please post your graphiteoneutils.py file.  It seems that there is some problem with that file.

dwende: What is the output of running
```
bash /opt/GraphiteOne/bin/graphiteone --ogl=yes
``` 
from the terminal

vincenzoo: what happens if you omit the --ogl=yes part?  I remember running into this, however I cannot remember what the solution was.  I am trying to recreate this problem, I will let you know if I find a solution

Slingshot: The encoding line has to be the first line of the file with no indentations at all

---

### Post by Slingshot on 2007-11-14
Hi **xethm55**

Still returning the same error. Im no python programmer, but isnt # used for comments in python?

```
File "/opt/GraphiteOne/lib/graphiteoneutils.py", line 802
SyntaxError: Non-ASCII character '\xf8' in file /opt/GraphiteOne/lib/graphiteoneutils.py on line 802, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

What version of Ubuntu are you running? Im running Gutsy. This is the line in question with the **for** loop

```

def TC_TextReplaceMetaChars(text):
	for metachars in [('%%c','ø'),('%%p','%c'%177),('%%d','%c'%176)]:
		text = text.replace(metachars[0],metachars[1])
	return text

```

I found this site [http://zeirus.wordpress.com/2007/07/18/graphiteone-sotto-ubuntu-gutsy-gibbon/]("http://zeirus.wordpress.com/2007/07/18/graphiteone-sotto-ubuntu-gutsy-gibbon/")  using google translator I think he suggest using this.

```
coding # = utf-8
```

that returns

```
john@forsaken:/opt/GraphiteOne/bin$ bash ./graphiteone --ogl=yes
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteone.py", line 15, in <module>
    from graphiteoneapplication import GOneApplication
  File "/opt/GraphiteOne/lib/graphiteoneapplication.py", line 1, in <module>
    coding # = utf-8
NameError: name 'coding' is not defined
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteonesplashscreen.py", line 16, in <module>
    from qt import Qt
  File "/opt/GraphiteOne/lib/qt.py", line 1, in <module>
    coding # = utf-8
NameError: name 'coding' is not defined
```

*EDIT* Nevermind. I re-installed the .deb packages and added the coding line as you suggested and like magic it worked. now just got to get my Solidworks focused brain around GraphiteOne. Many thanks **xethm55**

---

### Post by superchargingmachine on 2007-12-15
I just got GraphiteOne running.  It only took about 6 hours:-)
I found a couple of files that had bad characters in them "non-ascii text"
Both were zero's.

First in graphiteoneutils.py 
if you run graphiteone from a terminal it will tell you the line with the problem it's between 800-900 can't remeber exactly which one.
from a terminal
sudo -s
nautilus
find graphiteoneutils.py and change the permissions to read-write
gedit graphiteutils.py change the bad zero and save the file.

I found the same problem in graphiteonedxfreader.py
follow the procedure above and change the character.

After this the program launched.

I hope this helps!
Paul

---

### Post by superchargingmachine on 2007-12-16
I forgot one additional change I needed to make.

In usr/bin/
Open graphiteone and remove the "#" in the first line of the file. 
When you open the file the first line looks like this
#! /bin/sh
It should be as follows
! /bin/sh

BTW - I have thrown all different types of values at the variables below and haven't noticed any change.
ogl="yes"
fsaa_mode="0"
params=""
python="python"
mybase=/opt/GraphiteOne
paths=""

---

### Post by FriedChips on 2007-12-19
Thanks for this how-to. Would you mind if I posted this ( with a few modifications ) on fedora's forums. I will of course give you the credit.:)

---

### Post by hgodling on 2007-12-23
I have been trying to get GraphiteOne to work on 64 bit Gutsy.  However I am getting the error;

> Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteonesplashscreen.py", line 16, in ?
    from qt import Qt
  File "/opt/GraphiteOne/lib/qt.py", line 46, in ?
    import libsip
ImportError: /opt/GraphiteOne/lib/libsip.so: wrong ELF class: ELFCLASS32
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteone.py", line 15, in ?
    from graphiteoneapplication import GOneApplication
  File "/opt/GraphiteOne/lib/graphiteoneapplication.py", line 13, in ?
    import HPY
  File "/opt/GraphiteOne/lib/HPY.py", line 2, in ?
    import HPYc
ImportError: /opt/GraphiteOne/lib/HPYc.so: wrong ELF class: ELFCLASS32

I believe this is due to 64-bit python trying to execute the 32-bit libraries.  Does anyone know of a method to fix this?

Alternatively I have tried recompiling the libraries with; 
```
./build.sh --mode=compil
``` 
but then I get an error;
> basename: extra operand `/usr/lib/python2.5/config/libpython2.5.so'
Try `basename --help' for more information.
QT build skipped. Using QT from system.
make  targets  \
        "DRIVERS = -DOPENGL_DRIVER -DCGM_DRIVER -DCGM3_DRIVER -DHPGL_DRIVER -DHPGL2_DRIVER -DIMAGE_DRIVER -DPICT_DRIVER -DPOSTSCRIPT_DRIVER -DPRINTF_DRIVER -DX11_DRIVER" \
        "PLATFORM_SRCS = lnxdirop.c lnxdynam.c lnxenv.c lnxerro.c lnxexit.c lnxfappl.c lnxfilnm.c lnxfilop.c lnxstart.c lnxtime.c " \
        "PLATFORM_FLAGS = -DFREETYPE -DDYNAMIC_LOADER" \
        "PLATFORM = linux" \
        "CC = gcc" \
        "CFLAGS = -O -ansi -Wall -pipe -fno-strict-aliasing -Wno-parentheses -Wcomment -Wimplicit -Wshadow -Wpointer-arith -Wcast-align -Wwrite-strings -Waggregate-return -Wmissing-prototypes -Wmissing-declarations " \
        "INC = -I. -Ifreetype/include" \
        "LINKER = gcc" \
        "LIBS = " \
        "LFLAGS = -shared" \
        "OGL_DRV_LIBS = -lGLU -lGL" \
        "OGL_DRV_LFLAGS = -shared" \
        "SONAME = so" \
        "FREETYPELIB=freetype/linux/libhoopsfreetype.a" \
        "AR = ar" \
        "ARFLAGS = rc"
make[1]: Entering directory `/home/hgodling/graphiteone-1.3-1/gonelibs/3rdparty/HOOPS-1100/Dev_Tools/hoops_3dgs/source'
Building shareable library...gcc -o libhoops1100.so  -shared lnxdirop.o lnxdynam.o lnxenv.o lnxerro.o lnxexit.o lnxfappl.o lnxfilnm.o lnxfilop.o lnxstart.o lnxt
...
xgldrive.o zoomcam.o freetype/linux/libhoopsfreetype.a  -lGLU -lGL
/usr/bin/ld: lnxdirop.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
lnxdirop.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libhoops1100.so] Error 1
make[1]: Leaving directory `/home/hgodling/graphiteone-1.3-1/gonelibs/3rdparty/HOOPS-1100/Dev_Tools/hoops_3dgs/source'
make: *** [linux] Error 2

---

### Post by hgodling on 2007-12-24
Here is a fix for the problem which vincenzoo was describing in case anyone else has that issue.

> vincen-zoo@vincenzoo:/opt/GraphiteOne/lib$ graphiteone --ogl=yes
/usr/bin/graphiteone: 19: function: not found
usage : graphiteone [options]
Options:
--ogl=[yes|no] Enable/Disable OpenGL display driver (default is no).
--fsaa-mode=[0..5] Enable FSAA mode for nVidia graphic cards (experimental!).
--python=[python executable] The python executable to use (default is python).
--paths=[path:...] More entries for PYTHONPATH.

use the command;

```
sudo ln -sf /bin/bash /bin/sh
```

this comes from;[HTML]http://forum.ubuntu-fr.org/viewtopic.php?pid=989439[/HTML]

---

### Post by almoravid on 2008-01-09
```
/opt/GraphiteOne/lib/HPY.py:2: RuntimeWarning: Python C API version mismatch for module HPYc: This Python has API version 1013, module HPYc has version 1012.
  import HPYc
/opt/GraphiteOne/lib/qt.py:46: RuntimeWarning: Python C API version mismatch for module libsip: This Python has API version 1013, module libsip has version 1012.
  import libsip
/opt/GraphiteOne/lib/qt.py:50: RuntimeWarning: Python C API version mismatch for module libqtc: This Python has API version 1013, module libqtc has version 1012.
  import libqtc
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/opt/GraphiteOne/lib/qt.py:46: RuntimeWarning: Python C API version mismatch for module libsip: This Python has API version 1013, module libsip has version 1012.
  import libsip
/opt/GraphiteOne/lib/qt.py:50: RuntimeWarning: Python C API version mismatch for module libqtc: This Python has API version 1013, module libqtc has version 1012.
  import libqtc
/opt/GraphiteOne/lib/qtxml.py:38: RuntimeWarning: Python C API version mismatch for module libqtxmlc: This Python has API version 1013, module libqtxmlc has version 1012.
  import libqtxmlc
/opt/GraphiteOne/lib/oc.py:6: RuntimeWarning: Python C API version mismatch for module libocc: This Python has API version 1013, module libocc has version 1012.
  import libocc
GOneStatusBar : running without parametric design extension
GOnePersistentElement : running without parametric design extension
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteone.py", line 15, in <module>
    from graphiteoneapplication import GOneApplication
  File "/opt/GraphiteOne/lib/graphiteoneapplication.py", line 25, in <module>
    from graphiteoneframe import *
  File "/opt/GraphiteOne/lib/graphiteoneframe.py", line 21, in <module>
    from graphiteonemenudata import *
  File "/opt/GraphiteOne/lib/graphiteonemenudata.py", line 15, in <module>
    from graphiteonemenuwidget import *
  File "/opt/GraphiteOne/lib/graphiteonemenuwidget.py", line 16, in <module>
    from graphiteoneparteditor import *
  File "/opt/GraphiteOne/lib/graphiteoneparteditor.py", line 15, in <module>
    from graphiteonepartelement import GOnePartElement
  File "/opt/GraphiteOne/lib/graphiteonepartelement.py", line 22, in <module>
    from graphiteonepartshadowelement import GOnePartShadowElement
  File "/opt/GraphiteOne/lib/graphiteonepartshadowelement.py", line 18, in <module>
    from graphiteonetciohandler import GOneTCIOElementHandler
  File "/opt/GraphiteOne/lib/graphiteonetciohandler.py", line 25, in <module>
    from graphiteoneworkingplane import GOneWorkingPlane
  File "/opt/GraphiteOne/lib/graphiteoneworkingplane.py", line 19, in <module>
    from graphiteoneutils import TC_TrsfToHoopsMatrix
  File "/opt/GraphiteOne/lib/graphiteoneutils.py", line 801
SyntaxError: Non-ASCII character '\xf8' in file /opt/GraphiteOne/lib/graphiteoneutils.py on line 801, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

I got this output when i run graphiteone thru my terminal. Anyone can help me?

---

### Post by Thingymebob on 2008-01-11
with hgodling here, on 64bit gutsy with exactly the same errors.
```
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteone.py", line 15, in <module>
    from graphiteoneapplication import GOneApplication
  File "/opt/GraphiteOne/lib/graphiteoneapplication.py", line 13, in <module>
    import HPY
  File "/opt/GraphiteOne/lib/HPY.py", line 2, in <module>
    import HPYc
ImportError: /opt/GraphiteOne/lib/HPYc.so: wrong ELF class: ELFCLASS32
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteonesplashscreen.py", line 16, in <module>
    from qt import Qt
  File "/opt/GraphiteOne/lib/qt.py", line 46, in <module>
    import libsip
ImportError: /opt/GraphiteOne/lib/libsip.so: wrong ELF class: ELFCLASS32

```

---

### Post by xethm55 on 2008-01-23
> **FriedChips said:**
> Thanks for this how-to. Would you mind if I posted this ( with a few modifications ) on fedora's forums. I will of course give you the credit.:)

I would not mind if you posted in the Fedora forums, with credit of course.  However I would appreciate it if you made clear that this was written for Ubuntu in mind, as the Fedora file system may be different.

---

### Post by xethm55 on 2008-01-23
To those of you that have been having problems with this on 64 Bit Ubuntu, I have not tried this on there.  Examining your output, however gives me the impression that it does not like the fact you are running a 32 bit binary on a 64 bit OS.  I looked at the website and do not see any information on a 64 bit port of Graphiteone.  There may be a way to get this to run in a chrooted environment (similar to what people used to do to get flash and 32 bit firefox on 64 bit Ubuntu).  I however have never done this before, so I have no further information.

---

### Post by mosaic2s on 2008-02-12
first file - line is 801, second file line is 1138 to locate non-zero text.

thanks for this great thread. it really helped. graphiteone is running.

---

### Post by mciaccia on 2008-02-14
I am running Ubuntu Gutsy 32 bits. I followed this HOWTO, but like some of the other members, I had problems with API/libraries incompatibilities. I solved them installing libstdc++5 and python2.4 (my Ubuntu had  libstdc++6 and python2.5 installed). Now it runs flawlessly  :)

Thanks xethm55 for this HOWTO!.

---

### Post by doug1212 on 2008-02-19
Thank you xethm55 and others for the install walk through and thanks to Graphiteone for allowing us to use the program.

Now I have the program installed on gutsy 32 bit machine and and I can start it without error and have been using the program following a few exercises I found on the web, all ok untill I tried using the "styles" menu and I a get crash.

Here is the error, Is it a code problem? and anyone else seeing it?

Thanks, Doug.

```
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteonepropeditor.py", line 173, in paintCell
    if self.hasSubItems() and column == 0 :
  File "/opt/GraphiteOne/lib/graphiteonepropeditor.py", line 865, in hasSubItems
    return self.withComment
AttributeError: withComment
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteonepropeditor.py", line 431, in updateEditorSize
    self.resizeEvent( e )
  File "/opt/GraphiteOne/lib/graphiteonepropeditor.py", line 417, in resizeEvent
    self.currentItem().showEditor()
  File "/opt/GraphiteOne/lib/graphiteonepropeditor.py", line 872, in showEditor
    if self.lin == None:
AttributeError: lin
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteonepropeditor.py", line 173, in paintCell
    if self.hasSubItems() and column == 0 :
  File "/opt/GraphiteOne/lib/graphiteonepropeditor.py", line 865, in hasSubItems
    return self.withComment
AttributeError: withComment
QWidget::setMinimumSize: The smallest allowed size is (0,0)
QWidget::setMaximumSize: (unnamed/QPushButton) Negative sizes (23,-4) are not possible
QWidget::setMinimumSize: The smallest allowed size is (0,0)
QWidget::setMaximumSize: (unnamed/QPushButton) Negative sizes (23,-4) are not possible
QWidget::setMinimumSize: The smallest allowed size is (0,0)
QWidget::setMaximumSize: (unnamed/QPushButton) Negative sizes (23,-4) are not possible
QWidget::setMinimumSize: The smallest allowed size is (0,0)
QWidget::setMaximumSize: (unnamed/QPushButton) Negative sizes (23,-4) are not possible
ASSERT: "dl == d->drawables" in widgets/qlistview.cpp (3116)
/usr/bin/graphiteone: line 92:  8548 Segmentation fault      (core dumped) $python $mybase/lib/graphiteone.py $params

```

---

### Post by erwall on 2008-02-21
Thanks superchargingmachine, that did it!

---

### Post by rajendra on 2008-03-26
Hi,
 I've been going through this thread with interest, because I, too, am facing problems with GraphiteOne. I use Gutsy 32 bit. Here's my terminal output:

rajendra@rajendra-desktop:/opt/GraphiteOne/bin$ bash /opt/GraphiteOne/bin/graphiteone --ogl=yes
/opt/GraphiteOne/lib/HPY.py:2: RuntimeWarning: Python C API version mismatch for module HPYc: This Python has API version 1013, module HPYc has version 1012.
  import HPYc
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteonesplashscreen.py", line 16, in <module>
    from qt import Qt
  File "/opt/GraphiteOne/lib/qt.py", line 46, in <module>
    import libsip
ImportError: libqt-mt.so.3: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteone.py", line 15, in <module>
    from graphiteoneapplication import GOneApplication
  File "/opt/GraphiteOne/lib/graphiteoneapplication.py", line 18, in <module>
    from qt import QString
  File "/opt/GraphiteOne/lib/qt.py", line 46, in <module>
    import libsip
ImportError: libqt-mt.so.3: cannot open shared object file: No such file or directory
rajendra@rajendra-desktop:/opt/GraphiteOne/bin$ 


Can somebody help me?
Thanks in advance.

---

### Post by xethm55 on 2008-03-26
> ImportError: libqt-mt.so.3: cannot open shared object file: No such file or directory

Seems that you are missing a file called libqt-mt.so.3.  Doing a search on [http://packages.ubuntu.com](http://packages.ubuntu.com) for libqt-mt.so.3, shows that it will be created when installing a package named libqt3-mt.  To install this, simply go to synaptic and seach for libqt3-mt and install that, or from the command line enter:
```
sudo apt-get install libqt3-mt
``` 

Let me know if that solves the issue.
-Xethm55

---

### Post by zhost on 2008-04-25
> **hgodling said:**
> Here is a fix for the problem which vincenzoo was describing in case anyone else has that issue.



use the command;

```
sudo ln -sf /bin/bash /bin/sh
```

this comes from;[HTML]http://forum.ubuntu-fr.org/viewtopic.php?pid=989439[/HTML]

Or change the first line of /usr/bin/graphiteone from

#! /bin/sh

to

#! /bin/bash

(This lesser involves everything else)

zhost

---

### Post by gregers on 2008-05-22
OK
I changed:

In /opt/GraphiteOne/bin/graphiteone 
#!/bin/sh
to
!/bin/sh

In 
/opt/GraphiteOne/lib/graphiteonedxfreader.py
and
/opt/GraphiteOne/lib/graphiteoneutils.py
first line to:
# -*- coding: utf-8 -*-

And added to the menu application
bash /opt/GraphiteOne/bin/graphiteone --ogl=yes

And under Ubuntu 8.04 it works nice.

Thanks :)

---

### Post by kinemagician on 2008-05-24
I was able to install following your tutorial the GraphiteOne **without any** problem on my Ubuntu version 8.04.
I had only to install the libstdc++5-3.3-dev libraries using synaptic.

Thanks for the tutorial.

Ettore

---

### Post by kkjensen on 2008-10-31
I noticed the graphiteone website is offline....did this group/company stop operations or what?  Anyone have any idea?

---

### Post by jwhendy on 2008-12-16
Sorry to bump - easier than starting a whole new thread when people familiar with it are already subscribed... is there anyone who knows of a working current place to download graphite-one? Their site is down and the only other site I found with links for downloading is not working either ([http://www.caddit.net/grone/](http://www.caddit.net/grone/)).

Are there any distros anyone knows about with it in the repos? It'd be possible to get the package from another distro perhaps?

Anyone?


Thanks,
John

---

### Post by MuShoe on 2009-03-31
seems like the site is back up now.

[http://www.graphiteone-cad.com/page_download.php](http://www.graphiteone-cad.com/page_download.php)

---

### Post by Ber P on 2009-07-11
I've tried to install graphiteone 3.0.1, on ubuntu 9.04. Made .deb's from the Fedora-packages and installed with no problems at all. G1 starts, but when trying to make a new part, it exits with the following output (in the terminal - no error messages on screen)

```
ERROR:(F:PK_PARTITION_create_empty,C:931,CT:PK_ERROR_modeller_not_started,S:1,AN:0,AN:,AI:-1,E:0)
ERROR:(F:PK_PARTITION_make_pmark,C:931,CT:PK_ERROR_modeller_not_started,S:1,AN:0,AN:,AI:-1,E:0)
Segmentation fault

```

I've tried all the trix in this thread, but nothing changes.

Anyone else seen this?

---

