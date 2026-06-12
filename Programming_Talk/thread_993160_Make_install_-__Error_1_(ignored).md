---
title: "Make install -  Error 1 (ignored)"
date: 2008-11-25
forum: Programming Talk
---

### Post by S.G. on 2008-11-25
I don't know where this error comes from.

- I'm trying to install a Qt4 project. This is a new laptop (Asus Eee PC 1000 with Ubuntu eee), so maybe I simply need some package.

- I've had problems with qmake and moc and others because they were set by default to use Qt3. I have done *make clean*, because moc persisted to give strange problems, but maybe there is something else I should do to clean up before running qmake - make - make install again.

- I've been googling for quite a while, but this seems to be a very general error, so I don't know where to look now...

Well, here's the code, and thanks  in advance...

g++ -c -pipe -fpermissive -O2 -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DQT_NO_DEBUG -DQT_PLUGIN -DQT_SCRIPT_LIB -DQT_QT3SUPPORT_LIB -DQT3_SUPPORT -DQT_XML_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQDESIGNER_EXPORT_WIDGETS -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtXml -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I../.moc -I../.gui -o ../.obj/qewextensibledialog.o ../src/qewextensibledialog.cpp

(Some more similar g++ sentences, no output)

rm -f libqewextensibledialogs.so
g++ -Wl,--no-undefined -shared -o libqewextensibledialogs.so ../.obj/qewextensibledialog.o ../.obj/qewsimpledialog.o ../.obj/qewtabdialog.o ../.obj/qewtoolboxdialog.o ../.obj/qewtreeviewdialog.o ../.obj/qewdialogsplugin.o ../.obj/qewdialogpreviews.o ../.obj/moc_qewextensibledialog.o ../.obj/moc_qewsimpledialog.o ../.obj/moc_qewtabdialog.o ../.obj/moc_qewtoolboxdialog.o ../.obj/moc_qewtreeviewdialog.o ../.obj/moc_qewdialogsplugin.o ../.obj/qmake_image_collection.o   -L/usr/lib -lQtScript -lQt3Support -lQtXml -lQtGui -lQtCore -lQtDesigner -lpthread

install -m 755 -p /home/a/Documents/PFC/qew-4/src/qewdialogfactory.h /usr/include/qew/
strip /usr/include/qew/qewdialogfactory.h
strip: /usr/include/qew/qewdialogfactory.h: File format not recognized
make: [install_includes] Error 1 (ignored)

(Every install ends up with an Error 1)

The project is not installed.

Any thoughts?

---

### Post by dwhitney67 on 2008-11-25
The command "strip" is used to discard (debugging) symbols from object files.  The Makefile is passing a header file!

The error is ignored because the "strip" command (in the Makefile) is preceded with a minus sign ('-').

If you did not write the Makefile, I would not worry about the "error".  Think of it as a "warning".

Verify that the final product you seek is in /usr/include/qew/.

---

### Post by Keith Hedger on 2008-11-25
try ```
sudo make install
```

---

### Post by S.G. on 2008-11-25
> **dwhitney67 said:**
> The command "strip" is used to discard (debugging) symbols from object files.  The Makefile is passing a header file!

The error is ignored because the "strip" command (in the Makefile) is preceded with a minus sign ('-').

If you did not write the Makefile, I would not worry about the "error".  Think of it as a "warning".

Verify that the final product you seek is in /usr/include/qew/.

Thanks a lot for the help...

There is something there, but not exactly what I expected... and it doesn't work. 

I've remarked also this weird sentence during make install:
install -m 755 -p "libqewextensibledialogs.so" "//plugins/designer/libqewextensibledialogs.so"
strip --strip-unneeded "//plugins/designer/libqewextensibledialogs.so"

What can that double / mean?

---

### Post by dwhitney67 on 2008-11-25
The double slashes probably are the result of a missing, or poorly defined, Makefile variable.

For instance, if the following path were used, a double slash would precede the path name:
```

SOMEDIR = usr/lib
...
install:
        install -m 755 -p libqewextensibledialogs.so /$(SOMEDI)/plugins/designer/libqewextensibledialogs.so
...

```
Note how the SOMEDIR has been intentionally misspelled in the install statement.

Did you create the Makefile, or was it auto-generated?  If the latter, perhaps you need to specify --prefix when you perform a "configure".  If the former, then edit your Makefile to look for bugs.

---

### Post by S.G. on 2008-11-26
> **dwhitney67 said:**
> The double slashes probably are the result of a missing, or poorly defined, Makefile variable.

For instance, if the following path were used, a double slash would precede the path name:
```

SOMEDIR = usr/lib
...
install:
        install -m 755 -p libqewextensibledialogs.so /$(SOMEDI)/plugins/designer/libqewextensibledialogs.so
...

```
Note how the SOMEDIR has been intentionally misspelled in the install statement.

Did you create the Makefile, or was it auto-generated?  If the latter, perhaps you need to specify --prefix when you perform a "configure".  If the former, then edit your Makefile to look for bugs.

Thanks again... I'm not used to qmake. Maybe I'm missing something.

I did locate inside those three /$(QTDIR) where the // was appearing. Since 
```

$echo $QTDIR

```
gives 
```

/usr/share/qt4

```
I take the variable does have a value... and spelling was ok.

Nevertheless that was the problem, for I've harcoded QTDIR's value and have the project installed.

I wonder why make install wouldn't pick the value, though...

Thanks a lot.

---

### Post by dwhitney67 on 2008-11-26
> **S.G. said:**
> Thanks again... I'm not used to qmake. Maybe I'm missing something.

I did locate inside those three /$(QTDIR) where the // was appearing. Since 
```

$echo $QTDIR

```
gives 
```

/usr/share/qt4

```
I take the variable does have a value... and spelling was ok.

Nevertheless that was the problem, for I've harcoded QTDIR's value and have the project installed.

I wonder why make install wouldn't pick the value, though...

Thanks a lot.

That's interesting.  The Makefile should be able to reference your environment's variables, including QTDIR.

If you want to test a Makefile, write your own:
```

foo:
        @echo $(QTDIR)

```
There is a tab-space before the @ symbol.  When you are done saving the file as "Makefile", run 'make' on the command line.  This should print out the value of QTDIR.

---

