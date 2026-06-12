---
title: "Compiling QMC2 on Ubuntu 20.04"
date: 2020-04-27
forum: Packaging and Compiling Programs
---

### Post by Briga on 2020-04-27
Hi, I am trying to compile QMC2 (the mame frontend) in 20.04. 

After managing to install the dependencies it stills stop with many errors, the first one being:
```
In file included from lzma/7z.h:7,
                 from sevenzipfile.h:19,
                 from imagewidget.h:14,
                 from imagechecker.h:14,
                 from imagechecker.cpp:9:
lzma/7zTypes.h:98:15: error: expected identifier before numeric constant
   98 | #define False 0
      |               ^

```

Has any one succeed in doing it or can point me in the right direction since there is no package or PPA?

Thanks

---

### Post by Yellow Pasque on 2020-04-27
I tried it and I hit the same error. I had to use the latest version of QMC from their svn repo:
[http://wiki.batcom-it.net/index.php/The_%27ultimate%27_guide_to_QMC2#Building_and_installing_QMC2_from_source](http://wiki.batcom-it.net/index.php/The_%27ultimate%27_guide_to_QMC2#Building_and_installing_QMC2_from_source)
I also had to run 'make os-detect' before 'make' or I would get a ton of errors.

---

### Post by slickymaster on 2020-04-27
*Thread moved to **Packaging and Compiling Programs**.*

---

### Post by Briga on 2020-04-27
> **Yellow Pasque said:**
> I tried it and I hit the same error. I had to use the latest version of QMC from their svn repo:
[http://wiki.batcom-it.net/index.php/The_%27ultimate%27_guide_to_QMC2#Building_and_installing_QMC2_from_source](http://wiki.batcom-it.net/index.php/The_%27ultimate%27_guide_to_QMC2#Building_and_installing_QMC2_from_source)
I also had to run 'make os-detect' before 'make' or I would get a ton of errors.

Thanks, I tried also that way... via SVN 
```
svn co https://svn.code.sf.net/p/qmc2/code/trunk qmc2

```

and also the make os-detect which returns:

```
make os-detect
Operating System ............ Linux
Distribution / OS version ... Ubuntu_20.04
System information .......... Linux briga-laptop 5.4.0-26-generic #30-Ubuntu SMP Mon Apr 20 16:58:30 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
System cfg-file (ok) ........ arch/Linux.cfg
Distribution cfg-file (?) ... arch/Linux/Ubuntu_20.04.cfg

```

but as I hit make I get the same errors as before :(

---

### Post by Yellow Pasque on 2020-04-27
> **Briga said:**
> Thanks, I tried also that way... via SVN 
```
svn co https://svn.code.sf.net/p/qmc2/code/trunk qmc2

```

and also the make os-detect which returns:

```
make os-detect
Operating System ............ Linux
Distribution / OS version ... Ubuntu_20.04
System information .......... Linux briga-laptop 5.4.0-26-generic #30-Ubuntu SMP Mon Apr 20 16:58:30 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
System cfg-file (ok) ........ arch/Linux.cfg
Distribution cfg-file (?) ... arch/Linux/Ubuntu_20.04.cfg

```

but as I hit make I get the same errors as before :(

They shouldn't be the same errors. The first Please give a sample

---

### Post by Briga on 2020-04-28
> **Yellow Pasque said:**
> They shouldn't be the same errors. The first Please give a sample

The full list is quite long ... this is the beginning

```
In file included from lzma/7z.h:7,
                 from sevenzipfile.h:19,
                 from imagewidget.h:14,
                 from imagechecker.h:14,
                 from imagechecker.cpp:9:
lzma/7zTypes.h:98:15: error: expected identifier before numeric constant
   98 | #define False 0
      |               ^
lzma/7zTypes.h:98:15: error: expected ‘}’ before numeric constant
In file included from /usr/include/x86_64-linux-gnu/qt5/QtCore/qcborarray.h:43,
                 from /usr/include/x86_64-linux-gnu/qt5/QtCore/QtCore:37,
                 from /usr/include/x86_64-linux-gnu/qt5/QtGui/QtGuiDepends:3,
                 from /usr/include/x86_64-linux-gnu/qt5/QtGui/QtGui:3,
                 from machinelist.h:4,
                 from imagechecker.cpp:17:
/usr/include/x86_64-linux-gnu/qt5/QtCore/qcborvalue.h:104:21: note: to match this ‘{’
  104 |     enum Type : int {
      |                     ^
In file included from lzma/7z.h:7,
                 from sevenzipfile.h:19,
                 from imagewidget.h:14,
                 from imagechecker.h:14,
                 from imagechecker.cpp:9:
lzma/7zTypes.h:98:15: error: expected unqualified-id before numeric constant
   98 | #define False 0
      |               ^
In file included from /usr/include/x86_64-linux-gnu/qt5/QtCore/qobject.h:46,
                 from /usr/include/x86_64-linux-gnu/qt5/QtCore/qiodevice.h:45,
                 from /usr/include/x86_64-linux-gnu/qt5/QtCore/qfiledevice.h:43,
                 from /usr/include/x86_64-linux-gnu/qt5/QtCore/qfile.h:44,
                 from /usr/include/x86_64-linux-gnu/qt5/QtCore/qfileinfo.h:43,
                 from /usr/include/x86_64-linux-gnu/qt5/QtCore/qdir.h:44,
                 from /usr/include/x86_64-linux-gnu/qt5/QtWidgets/qfiledialog.h:44,
                 from /usr/include/x86_64-linux-gnu/qt5/QtWidgets/QFileDialog:1,
                 from imagechecker.cpp:1:
/usr/include/x86_64-linux-gnu/qt5/QtCore/qcborvalue.h:129:5: error: ‘friend’ used outside of class
  129 |     Q_ENUM(Type)
      |     ^~~~~~
(...)
make: *** [Makefile:1043: qmc2-bin] Error 2

```

---

### Post by Yellow Pasque on 2020-04-28
> lzma/7zTypes.h:98:15: error: expected identifier before numeric constant
   98 | #define False 0

Then you aren't using the SVN version, because this code was changed since the 0.195 release:
[https://sourceforge.net/p/qmc2/code/8308/tree//trunk/lzma/7zTypes.h?diff=50e96eaae88f3d248f63f3bb:8307](https://sourceforge.net/p/qmc2/code/8308/tree//trunk/lzma/7zTypes.h?diff=50e96eaae88f3d248f63f3bb:8307)

Are you sure you're in the correct directory? Did you delete the old 0.195 directory before doing svn checkout to avoid confusion?

---

### Post by Briga on 2020-04-29
> **Yellow Pasque said:**
> Then you aren't using the SVN version, because this code was changed since the 0.195 release:
[https://sourceforge.net/p/qmc2/code/8308/tree//trunk/lzma/7zTypes.h?diff=50e96eaae88f3d248f63f3bb:8307](https://sourceforge.net/p/qmc2/code/8308/tree//trunk/lzma/7zTypes.h?diff=50e96eaae88f3d248f63f3bb:8307)

Are you sure you're in the correct directory? Did you delete the old 0.195 directory before doing svn checkout to avoid confusion?

Thanks a lot, that was the issue. Some files may have been there. I wiped the folder and installed in a new one. 

Still I encounter few issues but managed to solve them and I put them here for the benefit of anyone who could face them too.


The process that worked for me was to install the dependencies including
```
sudo apt install qttools5-dev-tools
```

then getting the source via subversion:

```
svn co https://svn.code.sf.net/p/qmc2/code/trunk qmc2
```

and creating some symlinks to overcome errors

```
sudo ln -s /usr/bin/qmake /usr/local/bin/qmake-qt5

sudo ln -s /usr/lib/qt5/bin/lrelease /usr/lib/qt5/bin/lrelease-qt5

```

Finally I could build it and install it with:

```
make os-detect

make

sudo make install
```

Kudos to Yellow Pasque

---

### Post by Yellow Pasque on 2020-04-29
Yeah, I had to make those symlinks too. I thought it was just my build environment, but maybe this program is doing something odd with qmake?
Anyway, I'm glad you got it built. Enjoy.

---

