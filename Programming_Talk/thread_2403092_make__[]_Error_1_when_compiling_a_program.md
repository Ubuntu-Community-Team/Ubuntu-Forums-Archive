---
title: "make: *** [] Error 1 when compiling a program"
date: 2018-10-07
forum: Programming Talk
---

### Post by jpfontenelle on 2018-10-07
Hello everyone.

I am trying to compile this program on Ubuntu 18.04. 
It's a program to visualize/analize haplotype networks.

It is called PopArt and the .bz2 can be downloaded here: [http://popart.otago.ac.nz/downloads.shtml](http://popart.otago.ac.nz/downloads.shtml)
Instructions for compiling can be found here: [https://github.com/jessicawleigh/popart/blob/master/INSTALL](https://github.com/jessicawleigh/popart/blob/master/INSTALL)

I downloaded the tarball, opened it, installed the suggested packages for debian/ubuntu and changed the paths on the popart.pro as suggested.

Once I run qmake && make, I get the following error message: 

Makefile:736: recipe for target 'ColourDialog.o' failed
make: *** [ColourDialog.o] Error 1

I am running the process like this:

:~/Downloads/popart-1.7/src$ qmake -makefile LPSOLVEDIR=/usr/bin/lp_solve MARBLEDIR=/usr/bin/marble popart.pro
:~/Downloads/popart-1.7/src$ make

I've done some reading online and apparently might be something to do with CXX, CXXFLAGS or q++, but I couldn't find the fix.

Anyone have any ideal?

Cheers

JP

---

### Post by TheFu on 2018-10-07
qmake?  Are you sure that shouldn't be gmake?  Same for q++, shouldn't that be g++?

---

### Post by steeldriver on 2018-10-07
@TheFu:
```

qmake - cross-platform makefile generator for Qt

```

---

### Post by TheFu on 2018-10-08
> **steeldriver said:**
> @TheFu:
```

qmake - cross-platform makefile generator for Qt

```

Ah. Thanks. gmake was already pretty cross-platform.  We used it to compile on 12 different platforms, including Windows and MacOS, but that was long, long, ago.

So qmake is like autoconf?  [https://doc.qt.io/qt-5/qmake-manual.html](https://doc.qt.io/qt-5/qmake-manual.html) Yep. Seems so.  autoconf is far from perfect.  Very cool.

I looked at the error message a little closer.  Are there any spaces in the directory or names for any files that need to be quoted?

---

### Post by steeldriver on 2018-10-08
You're not really providing a large enough portion of the error message for us to see

However, I suspect the issue is your LPSOLVEDIR and MARBLEDIR variables. Looking at the linked instructions:

> 
However, if you've installed the lpsolve or Marble headers somewhere other than 
/usr/include/lpsolve and /usr/include/marble, you'll have to tell qmake where they are. 
You can do this by running the commands:

```
qmake -makefile LPSOLVEDIR=/path/to/lpsolve/lpsolve MARBLEDIR=/path/to/marble popart.pro
make
```


If you installed libmarble-dev and liblpsolve55-dev using apt, then they WILL be in /usr/include/lpsolve and /usr/include/marble and so you DON'T need to add the LPSOLVEDIR and MARBLEDIR parts to your qmake command

Even if you DID need to add them, they would not be the /bin (binary program) directories, but the /include (header) directories that you would add

---

### Post by spjackson on 2018-10-08
> **jpfontenelle said:**
> 
I am running the process like this:

:~/Downloads/popart-1.7/src$ qmake -makefile LPSOLVEDIR=/usr/bin/lp_solve MARBLEDIR=/usr/bin/marble popart.pro
:~/Downloads/popart-1.7/src$ make

I've done some reading online and apparently might be something to do with CXX, CXXFLAGS or q++, but I couldn't find the fix.

I did something similar after editing popart.pro as per the INSTALL instructions. The error I get with ColourDialog.o concerns constexpr. My initial guess was that the code is written to c++98 standard because the missing constexpr was new in c++11... so I added
```

QMAKE_CXXFLAGS += -std=c++98

```
to popart.pro. This successfully compiles ColourDialog.o but then fails on HapnetWindow.o because of "nullptr" and "override" which are used and were new in c++11. So the question is, what C++ standard is this code written to? That should probably be a question for the author, although the same question applies to the dependencies. Alternatively, what is the highest Ubuntu version on which the project will build out of the box?

You can convert the constexpr message to an error by adding -fpermissive to QMAKE_CXXFLAGS. My best effort is with
```

QMAKE_CXXFLAGS += -std=c++11 -fpermissive 

```
but it still chokes on HapnetWindow.o because /usr/include/marble/MarbleWidget.h declares 2 methods as override but they do not override anything.

At that point, I stop trying to guess.

---

### Post by jpfontenelle on 2018-10-08
I tried to add the LPSOLVEDIR and the MARBLEDIR part... when I added, I did a 'which lp_solve' and 'which marble' and got the /usr/bin/... ones. Maybe that was the problem? Will try.

---

### Post by jpfontenelle on 2018-10-08
For those who requested the full error:

```
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o AlignmentDelegate.o gui/AlignmentDelegate.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o AlignmentModel.o gui/AlignmentModel.cpp
gui/AlignmentModel.cpp: In constructor ‘AlignmentModel::AlignmentModel(std::vector<Sequence*>&, QObject*)’:
gui/AlignmentModel.cpp:30:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (int i = 0; i < _nchar; i++)
                   ~~^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual int AlignmentModel::rowCount(const QModelIndex&) const’:
gui/AlignmentModel.cpp:35:49: warning: unused parameter ‘parent’ [-Wunused-parameter]
 int AlignmentModel::rowCount(const QModelIndex &parent) const
                                                 ^~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual int AlignmentModel::columnCount(const QModelIndex&) const’:
gui/AlignmentModel.cpp:40:52: warning: unused parameter ‘parent’ [-Wunused-parameter]
 int AlignmentModel::columnCount(const QModelIndex &parent) const
                                                    ^~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual QVariant AlignmentModel::data(const QModelIndex&, int) const’:
gui/AlignmentModel.cpp:47:19: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (index.row() >= _nseq)  return QVariant();
       ~~~~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp:49:22: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (index.column() >= _nchar)  return QVariant();
       ~~~~~~~~~~~~~~~^~~~~~~~~
gui/AlignmentModel.cpp:56:24: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (index.column() >= _alignment.at(index.row())->length())
         ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:71:24: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (index.column() >= _mask.size())
         ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:77:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (index.row() >= _goodSeqs.size())
         ~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual QVariant AlignmentModel::headerData(int, Qt::Orientation, int) const’:
gui/AlignmentModel.cpp:99:18: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if  (section > _nchar)  return QVariant();
          ~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp:105:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (section > _nseq)  return QVariant();
         ~~~~~~~~^~~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual bool AlignmentModel::removeRows(int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:162:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (int i = 0; i < _nseq; i++)
                   ~~^~~~~~~
gui/AlignmentModel.cpp:163:33: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (_alignment[i]->length() > newnchar)
         ~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~
gui/AlignmentModel.cpp:168:16: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (newnchar < _nchar)
       ~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘int AlignmentModel::locateEndRev(int, int)’:
gui/AlignmentModel.cpp:190:30: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if ((*dnaiter)->length() > dnaseqlen)  dnaseqlen = (*dnaiter)->length();
         ~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual bool AlignmentModel::removeColumns(int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:246:26: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (unsigned i = 0; i < rowCount(); i++)
                        ~~^~~~~~~~~~~~
gui/AlignmentModel.cpp:248:14: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (last >= _alignment[i]->length())
         ~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:257:36: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
         if ((dnacolumn + dnacount) > _dnaAlignment[i]->length())
             ~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:271:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
         if (thisEnd > _dnaAlignment[i]->length())
             ~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:274:25: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
         if (!(thisStart >= _dnaAlignment[i]->length()))
               ~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:206:27: warning: unused variable ‘thisCount’ [-Wunused-variable]
   int thisStart, thisEnd, thisCount;
                           ^~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::addSequence(int, QString&)’:
gui/AlignmentModel.cpp:290:11: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (row > _nseq || row < 0)  return false;
       ~~~~^~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::addSequence(int, Sequence*)’:
gui/AlignmentModel.cpp:300:11: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (row > _nseq || row < 0)  return false;
       ~~~~^~~~~~~
gui/AlignmentModel.cpp:314:11: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (row == _nseq)
       ~~~~^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual bool AlignmentModel::insertColumns(int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:396:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (int i = 0; i < _nseq; i++)
                   ~~^~~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual bool AlignmentModel::insertColumns(int, QString&, const QModelIndex&)’:
gui/AlignmentModel.cpp:437:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (int i = 0; i < _nseq; i++)
                   ~~^~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::regionContainsNonGaps(int, int, int, int)’:
gui/AlignmentModel.cpp:456:14: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (bottom > _nseq || right >= _nchar)
       ~~~~~~~^~~~~~~
gui/AlignmentModel.cpp:456:31: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (bottom > _nseq || right >= _nchar)
                         ~~~~~~^~~~~~~~~
gui/AlignmentModel.cpp:463:36: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (_alignment.at(i)->length() <= right)
         ~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::deleteRange(int, int, int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:479:14: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (bottom >= _nseq || right >= _nchar)  return false;
       ~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp:479:32: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (bottom >= _nseq || right >= _nchar)  return false;
                          ~~~~~~^~~~~~~~~
gui/AlignmentModel.cpp:493:26: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (left == 0 && right == (_nchar - 1))
                    ~~~~~~^~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:496:31: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   else if (top == 0 && bottom == (_nseq - 1))
                        ~~~~~~~^~~~~~~~~~~~~~
gui/AlignmentModel.cpp:503:38: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (_alignment.at(i)->length() <= right)
           ~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp:513:34: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
           if (dnaleft + dnacount > _dnaAlignment.at(i)->length())
               ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:526:24: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
           if (dnaright > _dnaAlignment.at(i)->length())
               ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:529:25: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
           if (!(dnaleft >= _dnaAlignment.at(i)->length()))
                 ~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:542:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (int i = 0; i < _nseq; i++)
                   ~~^~~~~~~
gui/AlignmentModel.cpp:543:36: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (_alignment.at(i)->length() > newnchar)
         ~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~
gui/AlignmentModel.cpp:547:16: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (newnchar < _nchar)
       ~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::deleteCharacter(int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:567:11: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (col < _alignment.at(row)->length())
       ~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:581:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (dnacolumn < _dnaAlignment.at(row)->length())
           ~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:588:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (dnacolumn <= _dnaAlignment.at(row)->length())
           ~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:590:32: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       else if ((dnacolumn - 3) < _dnaAlignment.at(row)->length())
                ~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:576:9: warning: unused variable ‘dnacount’ [-Wunused-variable]
     int dnacount = 3;
         ^~~~~~~~
gui/AlignmentModel.cpp:599:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (int i = 0; i < _nseq; i++)
                   ~~^~~~~~~
gui/AlignmentModel.cpp:600:36: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (_alignment.at(i)->length() > newnchar)
         ~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~
gui/AlignmentModel.cpp:604:16: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (newnchar < _nchar)
       ~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::insertCharacter(char, int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:630:7: warning: variable ‘dnacolumn’ set but not used [-Wunused-but-set-variable]
   int dnacolumn;
       ^~~~~~~~~
gui/AlignmentModel.cpp:631:7: warning: unused variable ‘dnacount’ [-Wunused-variable]
   int dnacount = 3;
       ^~~~~~~~
gui/AlignmentModel.cpp:644:8: warning: variable ‘colinserted’ set but not used [-Wunused-but-set-variable]
   bool colinserted = false;
        ^~~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::insertCharacters(int, int, int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:688:32: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (topRow == 0 && bottomRow == (_nseq - 1))
                      ~~~~~~~~~~^~~~~~~~~~~~~~
gui/AlignmentModel.cpp:708:38: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (_alignment.at(i)->length() > maxSeqLen)
           ~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~
gui/AlignmentModel.cpp:719:39: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (_inTranslation && dnacolumn < _dnaAlignment.at(i)->length())
                             ~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::insertCharacters(int, int, int, QString&, const QModelIndex&)’:
gui/AlignmentModel.cpp:779:32: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (topRow == 0 && bottomRow == (_nseq - 1))
                      ~~~~~~~~~~^~~~~~~~~~~~~~
gui/AlignmentModel.cpp:787:38: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (_alignment.at(i)->length() > maxSeqLen)
           ~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::fetchCharacters(int, int, int, AlignmentModel::Direction)’:
gui/AlignmentModel.cpp:829:30: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     colsremain = (currentcol < (_nchar - 2));
                   ~~~~~~~~~~~^~~~~~~~~~~~~~
gui/AlignmentModel.cpp:838:23: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if ((currentcol >= _alignment.at(i)->length()) ||
            ~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::moveCharacters(int, int, int, int, int)’:
gui/AlignmentModel.cpp:899:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (right >= _alignment.at(i)->length())
           ~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:902:37: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
         while (rightSubseq.length() < (right - left + 1))
                ~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:913:30: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if ((lenSubseq + left) > _alignment.at(i)->length())
           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:922:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (right + distance >= _alignment.at(i)->length())
           ~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:925:37: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
         while (rightSubseq.length() < distance)
                ~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~
gui/AlignmentModel.cpp:936:30: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if ((lenSubseq + left) > _alignment.at(i)->length())
           ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:892:7: warning: unused variable ‘j’ [-Wunused-variable]
   int j;
       ^
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::pushCharacters(int, int, int, int, AlignmentModel::Direction)’:
gui/AlignmentModel.cpp:984:18: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (endcol >= (_alignment.at(i)->length() - 1))
           ~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:996:31: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (endcol <= 0 || endcol >= (_nchar - 1))
                        ~~~~~~~^~~~~~~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘void AlignmentModel::maskRows(int, int)’:
gui/AlignmentModel.cpp:1032:25: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (top < 0 || bottom >= _nseq || top > bottom)
                  ~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘void AlignmentModel::translateAgain(int, int)’:
gui/AlignmentModel.cpp:1133:16: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (newnchar < _nchar)
       ~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp:1141:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   else if (newnchar > _nchar)
            ~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘void AlignmentModel::maskTranslate(std::vector<bool>*, std::vector<bool>*, int)’:
gui/AlignmentModel.cpp:1186:24: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (protMaskSize < proteinMask->size())
           ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:1168:9: warning: unused variable ‘newnchar’ [-Wunused-variable]
     int newnchar = (dnaMask->size() - readingFrame  + 2) / 3 + 1;
         ^~~~~~~~
gui/AlignmentModel.cpp:1212:24: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (protMaskSize < proteinMask->size())
           ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:1162:7: warning: unused variable ‘insertAt’ [-Wunused-variable]
   int insertAt;
       ^~~~~~~~
gui/AlignmentModel.cpp: In member function ‘int AlignmentModel::translationHelper(std::vector<Sequence*>*, std::vector<Sequence*>*, int, int)’:
gui/AlignmentModel.cpp:1228:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (int i = 0; i < _nseq; i++)
                   ~~^~~~~~~
gui/AlignmentModel.cpp:1229:18: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (oldnchar < dnaAlignment->at(i)->length())
         ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:1241:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (int i = 0; i < _nseq; i++)
                   ~~^~~~~~~
gui/AlignmentModel.cpp: In member function ‘void AlignmentModel::toggleTranslation(int, int, bool)’:
gui/AlignmentModel.cpp:1323:23: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     for (int i = 0; i < _nseq; i++)
                     ~~^~~~~~~
gui/AlignmentModel.cpp:1325:41: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
       if (_dnaAlignment.at(i)->length() > newnchar)
           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘void AlignmentModel::setAlignment(std::vector<Sequence*>&)’:
gui/AlignmentModel.cpp:1397:30: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if ((*seqiter)->length() > newnchar)  newnchar = (*seqiter)->length();
         ~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~
gui/AlignmentModel.cpp:1428:16: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   if (newnchar > _nchar)
       ~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp:1433:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (newnseq > _nseq)
         ~~~~~~~~^~~~~~~
gui/AlignmentModel.cpp:1441:22: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     else if (newnseq < _nseq)
              ~~~~~~~~^~~~~~~
gui/AlignmentModel.cpp:1455:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   else if (newnchar < _nchar)
            ~~~~~~~~~^~~~~~~~
gui/AlignmentModel.cpp:1459:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (newnseq > _nseq)
         ~~~~~~~~^~~~~~~
gui/AlignmentModel.cpp:1467:22: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     else if (newnseq < _nseq)
              ~~~~~~~~^~~~~~~
gui/AlignmentModel.cpp:1483:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if (newnseq > _nseq)
         ~~~~~~~~^~~~~~~
gui/AlignmentModel.cpp:1491:22: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     else if (newnseq < _nseq)
              ~~~~~~~~^~~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual bool AlignmentModel::removeColumns(int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:204:7: warning: ‘dnacolumn’ may be used uninitialized in this function [-Wmaybe-uninitialized]
   int dnacolumn;
       ^~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::insertCharacters(int, int, int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:720:40: warning: ‘dnacolumn’ may be used uninitialized in this function [-Wmaybe-uninitialized]
         _dnaAlignment.at(i)->insertGaps(dnacolumn, dnacount);
         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘bool AlignmentModel::deleteRange(int, int, int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:526:24: warning: ‘dnaright’ may be used uninitialized in this function [-Wmaybe-uninitialized]
           if (dnaright > _dnaAlignment.at(i)->length())
               ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentModel.cpp:513:23: warning: ‘dnaleft’ may be used uninitialized in this function [-Wmaybe-uninitialized]
           if (dnaleft + dnacount > _dnaAlignment.at(i)->length())
               ~~~~~~~~^~~~~~~~~~
gui/AlignmentModel.cpp: In member function ‘virtual bool AlignmentModel::insertColumns(int, int, const QModelIndex&)’:
gui/AlignmentModel.cpp:392:17: warning: ‘dnacolumn’ may be used uninitialized in this function [-Wmaybe-uninitialized]
     maskiter += dnacolumn;
                 ^~~~~~~~~
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o AlignmentView.o gui/AlignmentView.cpp
gui/AlignmentView.cpp: In member function ‘virtual void AlignmentView::resizeColumnsToContents()’:
gui/AlignmentView.cpp:69:26: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (unsigned i = 0; i < model()->columnCount(); i++)
                        ~~^~~~~~~~~~~~~~~~~~~~~~~~
gui/AlignmentView.cpp: In member function ‘virtual void AlignmentView::resizeRowsToContents()’:
gui/AlignmentView.cpp:82:26: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (unsigned i = 0; i < model()->rowCount(); i++)
                        ~~^~~~~~~~~~~~~~~~~~~~~
gui/AlignmentView.cpp: In member function ‘void AlignmentView::columnsAdded(const QModelIndex&, int, int)’:
gui/AlignmentView.cpp:92:53: warning: unused parameter ‘parent’ [-Wunused-parameter]
 void AlignmentView::columnsAdded(const QModelIndex &parent, int start, int end)
                                                     ^~~~~~
gui/AlignmentView.cpp: In member function ‘void AlignmentView::rowsAdded(const QModelIndex&, int, int)’:
gui/AlignmentView.cpp:97:50: warning: unused parameter ‘parent’ [-Wunused-parameter]
 void AlignmentView::rowsAdded(const QModelIndex &parent, int start, int end)
                                                  ^~~~~~
gui/AlignmentView.cpp: In member function ‘virtual void AlignmentView::mouseMoveEvent(QMouseEvent*)’:
gui/AlignmentView.cpp:226:13: warning: variable ‘visRect’ set but not used [-Wunused-but-set-variable]
       QRect visRect = viewport()->contentsRect();
             ^~~~~~~
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o Assistant.o gui/Assistant.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o BarchartItem.o gui/BarchartItem.cpp
gui/BarchartItem.cpp: In member function ‘virtual void BarchartItem::paint(QPainter*, const QStyleOptionGraphicsItem*, QWidget*)’:
gui/BarchartItem.cpp:65:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     for (unsigned i = 0; i < _traits.size(); i++)
                          ~~^~~~~~~~~~~~~~~~
gui/BarchartItem.cpp:26:77: warning: unused parameter ‘option’ [-Wunused-parameter]
 chartItem::paint(QPainter *painter, const QStyleOptionGraphicsItem *option, QWidget *widget)
                                                                     ^~~~~~
gui/BarchartItem.cpp:26:94: warning: unused parameter ‘widget’ [-Wunused-parameter]
 int(QPainter *painter, const QStyleOptionGraphicsItem *option, QWidget *widget)
                                                                         ^~~~~~
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o BorderRectItem.o gui/BorderRectItem.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o CitationDialog.o gui/CitationDialog.cpp
gui/CitationDialog.cpp: In static member function ‘static QString CitationDialog::CitationRecord::formatAuthor(const QString&, CitationDialog::CitationRecord::CitationFormat)’:
gui/CitationDialog.cpp:394:13: warning: this ‘else’ clause does not guard... [-Wmisleading-indentation]
             else
             ^~~~
gui/CitationDialog.cpp:396:11: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the ‘else’
           initials = QString();
           ^~~~~~~~
gui/CitationDialog.cpp: In member function ‘QString CitationDialog::CitationRecord::formatCitation(CitationDialog::CitationRecord::CitationFormat) const’:
gui/CitationDialog.cpp:559:5: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
     if (_issue >= 0)
     ^~
gui/CitationDialog.cpp:562:4: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the ‘if’
    if (_startP >= 0)
    ^~
gui/CitationDialog.cpp:591:5: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
     if (_issue >= 0)
     ^~
gui/CitationDialog.cpp:594:4: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the ‘if’
    if (_startP >= 0)
    ^~
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o ColourDialog.o gui/ColourDialog.cpp
In file included from gui/NetworkModel.h:20:0,
                 from gui/NetworkLayout.h:4,
                 from gui/NetworkView.h:11,
                 from gui/ColourDialog.cpp:4:
gui/NetworkItem.h:21:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkItem::VERTWEIGHT’ of non-integral type [-fpermissive]
   static const double VERTWEIGHT = 1;
                       ^~~~~~~~~~
gui/NetworkItem.h:22:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkItem::VERTRAD’ of non-integral type [-fpermissive]
   static const double VERTRAD = 15;
                       ^~~~~~~
gui/NetworkItem.h:23:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkItem::EDGELENGTH’ of non-integral type [-fpermissive]
   static const double EDGELENGTH = 50;
                       ^~~~~~~~~~
In file included from gui/NetworkView.h:11:0,
                 from gui/ColourDialog.cpp:4:
gui/NetworkLayout.h:26:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::GOODENOUGH’ of non-integral type [-fpermissive]
   static const double GOODENOUGH = 1E-4;
                       ^~~~~~~~~~
gui/NetworkLayout.h:150:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::VERYSMALL’ of non-integral type [-fpermissive]
   static const double VERYSMALL = 1E-8;
                       ^~~~~~~~~
gui/NetworkLayout.h:151:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::FAIRLYSMALL’ of non-integral type [-fpermissive]
   static const double FAIRLYSMALL = 1E-6;
                       ^~~~~~~~~~~
gui/NetworkLayout.h:152:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::SMALL’ of non-integral type [-fpermissive]
   static const double SMALL = 1E-4;
                       ^~~~~
gui/NetworkLayout.h:157:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::BARNESHUTTHETA’ of non-integral type [-fpermissive]
   static const double BARNESHUTTHETA = 0.7;
                       ^~~~~~~~~~~~~~
gui/NetworkLayout.h:158:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::RESTARTTHRESHOLD’ of non-integral type [-fpermissive]
   static const double RESTARTTHRESHOLD = 0.2;
                       ^~~~~~~~~~~~~~~~
gui/NetworkLayout.h:159:23: error: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::MAXCOS’ of non-integral type [-fpermissive]
   static const double MAXCOS = 0.5;
                       ^~~~~~
Makefile:736: recipe for target 'ColourDialog.o' failed
make: *** [ColourDialog.o] Error 1
```

---

### Post by jpfontenelle on 2018-10-08
> **steeldriver said:**
> You're not really providing a large enough portion of the error message for us to see

However, I suspect the issue is your LPSOLVEDIR and MARBLEDIR variables. Looking at the linked instructions:



If you installed libmarble-dev and liblpsolve55-dev using apt, then they WILL be in /usr/include/lpsolve and /usr/include/marble and so you DON'T need to add the LPSOLVEDIR and MARBLEDIR parts to your qmake command

Even if you DID need to add them, they would not be the /bin (binary program) directories, but the /include (header) directories that you would add

Tried with the /usr/include/ paths and still didn't work.

---

### Post by jpfontenelle on 2018-10-08
> **spjackson said:**
> I did something similar after editing popart.pro as per the INSTALL instructions. The error I get with ColourDialog.o concerns constexpr. My initial guess was that the code is written to c++98 standard because the missing constexpr was new in c++11... so I added
```

QMAKE_CXXFLAGS += -std=c++98

```
to popart.pro. This successfully compiles ColourDialog.o but then fails on HapnetWindow.o because of "nullptr" and "override" which are used and were new in c++11. So the question is, what C++ standard is this code written to? That should probably be a question for the author, although the same question applies to the dependencies. Alternatively, what is the highest Ubuntu version on which the project will build out of the box?

You can convert the constexpr message to an error by adding -fpermissive to QMAKE_CXXFLAGS. My best effort is with
```

QMAKE_CXXFLAGS += -std=c++11 -fpermissive 

```
but it still chokes on HapnetWindow.o because /usr/include/marble/MarbleWidget.h declares 2 methods as override but they do not override anything.

At that point, I stop trying to guess.


After trying both these alternatives, this is the output/error I get:

```
/usr/lib/x86_64-linux-gnu/qt4/bin/qmake LPSOLVEDIR=/usr/include/lpsolve MARBLEDIR=/usr/include/marble -o Makefile popart.pro
g++ -c -m64 -pipe -std=c++11 -fpermissive -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o HapnetWindow.o gui/HapnetWindow.cpp
In file included from gui/HapnetWindow.h:28:0,
                 from gui/HapnetWindow.cpp:52:
seqio/GeoTrait.h:93:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double GeoTrait::SMALL&#8217; of non-integral type [-fpermissive]
   const static double SMALL = 1E-6;
                       ^~~~~
In file included from gui/HapLayer.h:9:0,
                 from gui/MapView.h:11,
                 from gui/HapnetWindow.h:29,
                 from gui/HapnetWindow.cpp:52:
/usr/include/marble/MarbleWidget.h:1138:10: error: &#8216;void Marble::MarbleWidget::connectNotify(const QMetaMethod&)&#8217; marked &#8216;override&#8217;, but does not override
     void connectNotify(const QMetaMethod &signal) override;
          ^~~~~~~~~~~~~
/usr/include/marble/MarbleWidget.h:1139:10: error: &#8216;void Marble::MarbleWidget::disconnectNotify(const QMetaMethod&)&#8217; marked &#8216;override&#8217;, but does not override
     void disconnectNotify(const QMetaMethod &signal) override;
          ^~~~~~~~~~~~~~~~
In file included from gui/NetworkModel.h:20:0,
                 from gui/NetworkLayout.h:4,
                 from gui/NetworkView.h:11,
                 from gui/MapView.h:14,
                 from gui/HapnetWindow.h:29,
                 from gui/HapnetWindow.cpp:52:
gui/NetworkItem.h:21:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkItem::VERTWEIGHT&#8217; of non-integral type [-fpermissive]
   static const double VERTWEIGHT = 1;
                       ^~~~~~~~~~
gui/NetworkItem.h:22:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkItem::VERTRAD&#8217; of non-integral type [-fpermissive]
   static const double VERTRAD = 15;
                       ^~~~~~~
gui/NetworkItem.h:23:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkItem::EDGELENGTH&#8217; of non-integral type [-fpermissive]
   static const double EDGELENGTH = 50;
                       ^~~~~~~~~~
In file included from gui/NetworkView.h:11:0,
                 from gui/MapView.h:14,
                 from gui/HapnetWindow.h:29,
                 from gui/HapnetWindow.cpp:52:
gui/NetworkLayout.h:26:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkLayout::GOODENOUGH&#8217; of non-integral type [-fpermissive]
   static const double GOODENOUGH = 1E-4;
                       ^~~~~~~~~~
gui/NetworkLayout.h:150:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkLayout::VERYSMALL&#8217; of non-integral type [-fpermissive]
   static const double VERYSMALL = 1E-8;
                       ^~~~~~~~~
gui/NetworkLayout.h:151:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkLayout::FAIRLYSMALL&#8217; of non-integral type [-fpermissive]
   static const double FAIRLYSMALL = 1E-6;
                       ^~~~~~~~~~~
gui/NetworkLayout.h:152:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkLayout::SMALL&#8217; of non-integral type [-fpermissive]
   static const double SMALL = 1E-4;
                       ^~~~~
gui/NetworkLayout.h:157:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkLayout::BARNESHUTTHETA&#8217; of non-integral type [-fpermissive]
   static const double BARNESHUTTHETA = 0.7;
                       ^~~~~~~~~~~~~~
gui/NetworkLayout.h:158:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkLayout::RESTARTTHRESHOLD&#8217; of non-integral type [-fpermissive]
   static const double RESTARTTHRESHOLD = 0.2;
                       ^~~~~~~~~~~~~~~~
gui/NetworkLayout.h:159:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double NetworkLayout::MAXCOS&#8217; of non-integral type [-fpermissive]
   static const double MAXCOS = 0.5;
                       ^~~~~~
In file included from gui/HapnetWindow.h:32:0,
                 from gui/HapnetWindow.cpp:52:
popgen/Statistics.h:109:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double Statistics::EPS&#8217; of non-integral type [-fpermissive]
   const static double EPS = 3.0e-7;
                       ^~~
popgen/Statistics.h:110:23: warning: &#8216;constexpr&#8217; needed for in-class initialization of static data member &#8216;const double Statistics::FPMIN&#8217; of non-integral type [-fpermissive]
   const static double FPMIN = 1.0e-30;
                       ^~~~~
In file included from gui/HapnetWindow.cpp:57:0:
gui/GroupItemDialog.h:157:15: warning: &#8216;template<class> class std::auto_ptr&#8217; is deprecated [-Wdeprecated-declarations]
   static std::auto_ptr<QIcon> _lockedIcon;// = 0;
               ^~~~~~~~
In file included from /usr/include/c++/7/bits/locale_conv.h:41:0,
                 from /usr/include/c++/7/locale:43,
                 from /usr/include/c++/7/iomanip:43,
                 from gui/HapnetWindow.cpp:44:
/usr/include/c++/7/bits/unique_ptr.h:51:28: note: declared here
   template<typename> class auto_ptr;
                            ^~~~~~~~
Makefile:835: recipe for target 'HapnetWindow.o' failed
make: *** [HapnetWindow.o] Error 1
```

---

### Post by spjackson on 2018-10-08
> **jpfontenelle said:**
> 
In file included from gui/HapLayer.h:9:0,
                 from gui/MapView.h:11,
                 from gui/HapnetWindow.h:29,
                 from gui/HapnetWindow.cpp:52:
/usr/include/marble/MarbleWidget.h:1138:10: error: ‘void Marble::MarbleWidget::connectNotify(const QMetaMethod&)’ marked ‘override’, but does not override
     void connectNotify(const QMetaMethod &signal) override;
          ^~~~~~~~~~~~~
/usr/include/marble/MarbleWidget.h:1139:10: error: ‘void Marble::MarbleWidget::disconnectNotify(const QMetaMethod&)’ marked ‘override’, but does not override
     void disconnectNotify(const QMetaMethod &signal) override;
          ^~~~~~~~~~~~~~~~


Precisely. As I said "it still chokes on HapnetWindow.o because  /usr/include/marble/MarbleWidget.h declares 2 methods as override but  they do not override anything".

So I did a bit more research... /usr/include/marble/MarbleWidget.h is compatible with Qt5 where QObject::connectNotify and QObject::disconnectNotify have the above signatures. It is not compatible with Qt4 where these methods have different signatures. I can't see a marble-dev package on 18.04 that is compatible with Qt4. Assuming there isn't one, you'd need to build Qt4 marble from source and use that in the .pro instead of the packaged Qt5 one.

---

### Post by jpfontenelle on 2018-10-16
> **spjackson said:**
> Precisely. As I said "it still chokes on HapnetWindow.o because  /usr/include/marble/MarbleWidget.h declares 2 methods as override but  they do not override anything".

So I did a bit more research... /usr/include/marble/MarbleWidget.h is compatible with Qt5 where QObject::connectNotify and QObject::disconnectNotify have the above signatures. It is not compatible with Qt4 where these methods have different signatures. I can't see a marble-dev package on 18.04 that is compatible with Qt4. Assuming there isn't one, you'd need to build Qt4 marble from source and use that in the .pro instead of the packaged Qt5 one.


Thanks for the help! 

I just need to figure out how to do that now... hahaha .. Any places you could recommend I could refer to?

Cheers

JP

---

### Post by norobro on 2018-10-16
I don't know anything about this program, so no guarantee on functionality, but I got it to compile against the Qt5 libraries by making the following changes.


Project file diff:
```
--- original.pro        2015-05-22 23:21:33.000000000 -0500
+++ popart.pro  2018-10-16 10:51:53.136049614 -0500
@@ -4,11 +4,13 @@
 
 TEMPLATE = app
 TARGET = popart
+LIBS += -ldl -lcolamd
 DEPENDPATH += . gui networks popgen seqio tree 
 INCLUDEPATH += . networks seqio popgen tree gui 
-DEFINES += NET_QT
+DEFINES += NET_QT QT_DISABLE_DEPRECATED_BEFORE=0x000000
+QMAKE_CXXFLAGS += -fpermissive
 CONFIG += qt warn_on release
-QT += svg
+QT += svg widgets core printsupport
 
 # default directory for lp_solve headers
 unix:!macx{
@@ -35,7 +37,7 @@
   error( "Marble headers not found!" )
   }
   
-  LIBS += -llpsolve55 -lmarblewidget
+  LIBS += -llpsolve55 -lmarblewidget-qt5
   #QMAKE_POST_LINK = build_help.sh
 }

```Additional changes:```
src/gui/NetworkView.cpp:7: //#include <QtConcurrentMap> // removed from Qt5
src/gui/GroupItemDialog.cpp:20: #include <QtCore>

```

---

### Post by jpfontenelle on 2018-10-16
> **norobro said:**
> I don't know anything about this program, so no guarantee on functionality, but I got it to compile against the Qt5 libraries by making the following changes.


Project file diff:
```
--- original.pro        2015-05-22 23:21:33.000000000 -0500
+++ popart.pro  2018-10-16 10:51:53.136049614 -0500
@@ -4,11 +4,13 @@
 
 TEMPLATE = app
 TARGET = popart
+LIBS += -ldl -lcolamd
 DEPENDPATH += . gui networks popgen seqio tree 
 INCLUDEPATH += . networks seqio popgen tree gui 
-DEFINES += NET_QT
+DEFINES += NET_QT QT_DISABLE_DEPRECATED_BEFORE=0x000000
+QMAKE_CXXFLAGS += -fpermissive
 CONFIG += qt warn_on release
-QT += svg
+QT += svg widgets core printsupport
 
 # default directory for lp_solve headers
 unix:!macx{
@@ -35,7 +37,7 @@
   error( "Marble headers not found!" )
   }
   
-  LIBS += -llpsolve55 -lmarblewidget
+  LIBS += -llpsolve55 -lmarblewidget-qt5
   #QMAKE_POST_LINK = build_help.sh
 }

```Additional changes:```
src/gui/NetworkView.cpp:7: //#include <QtConcurrentMap> // removed from Qt5
src/gui/GroupItemDialog.cpp:20: #include <QtCore>

```


Hey man, thanks for the help.

I tried to make the same alterations you made, but with no success. Still not compiling. 

Here is my popart.pro after edits:

```
######################################################################
# Automatically generated by qmake (2.01a) Sat Mar 17 11:24:10 2012
######################################################################


TEMPLATE = app
TARGET = popart
LIBS += -ldl -lcolamd
DEFINES += NET_QT QT_DISABLE_DEPRECATED_BEFORE=0x000000
QMAKE_CXXFLAGS += -fpermissive
 CONFIG += qt warn_on release
QT += svg widgets core printsupport


# default directory for lp_solve headers
unix:!macx{
  PRELPSOLVEDIR=/usr/include/lpsolve
  PREMARBLEDIR=/usr/include/marble


  exists($$PRELPSOLVEDIR/lp_lib.h){
  DEPENDPATH += $$PRELPSOLVEDIR
  INCLUDEPATH += $$PRELPSOLVEDIR
  } else:exists($$LPSOLVEDIR/lp_lib.h ) {
  DEPENDPATH += $$LPSOLVEDIR
  INCLUDEPATH += $$LPSOLVEDIR
      } else {
  error( "lpsolve headers not found!" )
  }


  exists($$PREMARBLEDIR/MarbleWidget.h){
  DEPENDPATH += $$PREMARBLEDIR
  INCLUDEPATH += $$PREMARBLEDIR
  } else:exists($$MARBLEDIR/MarbleWidget.h ) {
  DEPENDPATH += $$MARBLEDIR
  INCLUDEPATH += $$MARBLEDIR
      } else {
  error( "Marble headers not found!" )
  }
  
  LIBS += -L/usr/lib/lp_solve/ -llpsolve55 -lmarblewidget-qt5
  QMAKE_RPATHDIR += /usr/lib/lp_solve/
  #QMAKE_POST_LINK = build_help.sh
}


macx{
  ICON = popart.icns
  INCLUDEPATH += /usr/local/include/lpsolve /usr/local/include/marble
  LIBS += -llpsolve55 -lmarblewidget


  RC_FILE = popart.rc
  QMAKE_MACOSX_DEPLOYMENT_TARGET = 10.6
  QMAKE_MAC_SDK = macosx10.6
}


win32{
  INCLUDEPATH += "c:/lpsolve55" "c:/marble/marble"
  LIBS += "c:/lpsolve55/lpsolve55.lib" "c:/marble/libmarblewidget.dll"
  CONFIG += exceptions rtti #static static-libgcc
  RC_FILE = popart.rc


}


# Input
HEADERS += gui/AlignmentDelegate.h \
           gui/AlignmentModel.h \
           gui/AlignmentView.h \
           gui/Assistant.h \
           gui/BarchartItem.h \
           gui/BorderRectItem.h \
           gui/CitationDialog.h \
           gui/ColourDialog.h \
           gui/ColourTheme.h \
           gui/EdgeItem.h \
           gui/GroupItemDialog.h \
           gui/HapnetWindow.h \
           gui/HapAppError.h \
           gui/HapLayer.h \
           gui/HapLocation.h \
           gui/LabelItem.h \
           gui/LegendItem.h \
           gui/MapLegendDialog.h \
           gui/MapLegendWidget.h \
           gui/MapView.h \
           gui/MonospaceMessageBox.h \
           gui/MoveCommand.h \
           gui/NetworkItem.h \
           gui/NetworkLayout.h \
           gui/NetworkModel.h \
           gui/NetworkScene.h \
           gui/NetworkView.h \
           gui/SelectionRange.h \
           gui/TaxBoxItem.h \
           gui/TraitItem.h \
           gui/TraitModel.h \
           gui/TraitView.h \
           gui/VertexItem.h \
           gui/XPM.h \
           networks/AbstractMSN.h \
           networks/AncestralSeqNet.h \
           networks/ConcreteHapNet.h \
           networks/Edge.h \
           networks/Graph.h \
           networks/HapNet.h \
           networks/IntNJ.h \
           networks/MinSpanNet.h \
           networks/MedJoinNet.h \
           networks/NetworkError.h \
           networks/Vertex.h \
           networks/ParsimonyNet.h \
           networks/TCS.h \
           networks/TightSpanWalker.h \
           popgen/Statistics.h \
           popgen/StatsError.h \
           seqio/GeneticCode.h \
           seqio/GeoTrait.h \
           seqio/NexusParser.h \
           seqio/ParserTools.h \
           seqio/PhylipParser.h \
           seqio/SeqParseError.h \
           seqio/SeqParser.h \
           seqio/Sequence.h \
           seqio/SequenceError.h \
           seqio/TableParser.h \
           seqio/Trait.h \
           tree/ParsimonyNode.h \
           tree/ParsimonyTree.h \
           tree/SeqNode.h \
           tree/SeqTree.h \
           tree/Tree.h \
           tree/TreeError.h \
           tree/TreeNode.h 
SOURCES += gui/AlignmentDelegate.cpp \
           gui/AlignmentModel.cpp \
           gui/AlignmentView.cpp \
           gui/Assistant.cpp \
           gui/BarchartItem.cpp \
           gui/BorderRectItem.cpp \
           gui/CitationDialog.cpp \
           gui/ColourDialog.cpp \
           gui/ColourTheme.cpp \
           gui/EdgeItem.cpp \
           gui/GroupItemDialog.cpp \
           gui/HapnetWindow.cpp \
           gui/HapApp.cpp \
           gui/HapAppError.cpp \
           gui/HapLayer.cpp \
           gui/HapLocation.cpp \
           gui/LabelItem.cpp \
           gui/LegendItem.cpp \
           gui/MapLegendDialog.cpp \
           gui/MapLegendWidget.cpp \
           gui/MapView.cpp \
           gui/MonospaceMessageBox.cpp \
           gui/MoveCommand.cpp \
           gui/NetworkItem.cpp \
           gui/NetworkLayout.cpp \
           gui/NetworkModel.cpp \
           gui/NetworkScene.cpp \
           gui/NetworkView.cpp \
           gui/SelectionRange.cpp \
           gui/TaxBoxItem.cpp \
           gui/TraitItem.cpp \
           gui/TraitModel.cpp \
           gui/TraitView.cpp \
           gui/VertexItem.cpp \
           networks/AbstractMSN.cpp \
           networks/AncestralSeqNet.cpp \
           networks/ConcreteHapNet.cpp \
           networks/Edge.cpp \
           networks/Graph.cpp \
           networks/HapNet.cpp \
           networks/IntNJ.cpp \
           networks/MinSpanNet.cpp \
           networks/MedJoinNet.cpp \
           networks/NetworkError.cpp \
           networks/Vertex.cpp \
           networks/ParsimonyNet.cpp \
           networks/TCS.cpp \
           popgen/Statistics.cpp \
           popgen/StatsError.cpp \
           networks/TightSpanWalker.cpp \
           seqio/GeneticCode.cpp \
           seqio/GeoTrait.cpp \
           seqio/NexusParser.cpp \
           seqio/ParserTools.cpp \
           seqio/PhylipParser.cpp \
           seqio/SeqParseError.cpp \
           seqio/SeqParser.cpp \
           seqio/Sequence.cpp \
           seqio/SequenceError.cpp \
           seqio/TableParser.cpp \
           seqio/Trait.cpp \
           tree/ParsimonyNode.cpp \
           tree/ParsimonyTree.cpp \
           tree/SeqNode.cpp \
           tree/SeqTree.cpp \
           tree/Tree.cpp \
           tree/TreeError.cpp \
           tree/TreeNode.cpp
```

---

### Post by norobro on 2018-10-16
> **jpfontenelle said:**
> Hey man, thanks for the help.You're welcome.

It looks like you are missing a few things in your pro file. Here's mine:```
[FONT=monospace][COLOR=#000000]######################################################################[/COLOR]
# Automatically generated by qmake (2.01a) Sat Mar 17 11:24:10 2012
######################################################################

TEMPLATE = app
TARGET = popart
LIBS += -ldl -lcolamd
[COLOR="#FF0000"]DEPENDPATH += . gui networks popgen seqio tree  
INCLUDEPATH += . networks seqio popgen tree gui[/COLOR]  
DEFINES += NET_QT QT_DISABLE_DEPRECATED_BEFORE=0x000000
QMAKE_CXXFLAGS += -fpermissive
CONFIG += qt warn_on release
QT += svg widgets core printsupport [COLOR="#FF0000"]concurrent[/COLOR]

# default directory for lp_solve headers
##### identical from here to EOF
[/FONT]
```
If making these changes doesn't work please post the error messages you get surrounded buy code tags.

---

### Post by spjackson on 2018-10-17
And, of course, you will need to have installed Qt5's development tools & libraries and be using Qt5's qmake.

---

### Post by jpfontenelle on 2018-10-18
> **norobro said:**
> You're welcome.

It looks like you are missing a few things in your pro file. Here's mine:```
[FONT=monospace][COLOR=#000000]######################################################################[/COLOR]
# Automatically generated by qmake (2.01a) Sat Mar 17 11:24:10 2012
######################################################################

TEMPLATE = app
TARGET = popart
LIBS += -ldl -lcolamd
[COLOR=#FF0000]DEPENDPATH += . gui networks popgen seqio tree  
INCLUDEPATH += . networks seqio popgen tree gui[/COLOR]  
DEFINES += NET_QT QT_DISABLE_DEPRECATED_BEFORE=0x000000
QMAKE_CXXFLAGS += -fpermissive
CONFIG += qt warn_on release
QT += svg widgets core printsupport [COLOR=#FF0000]concurrent[/COLOR]

# default directory for lp_solve headers
##### identical from here to EOF
[/FONT]
```
If making these changes doesn't work please post the error messages you get surrounded buy code tags.

For some reason, the forum is not allowing me to post the whole output of the failed make in a code tag

But it didn't work.

The final error is:
```
g++ -c -m64 -pipe -fpermissive -O2 -Wall -W -D_REENTRANT -DNET_QT -DQT_DISABLE_DEPRECATED_BEFORE=0x000000 -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -I/usr/include/lpsolve -I/usr/include/marble -I. -o HapnetWindow.o gui/HapnetWindow.cppIn file included from gui/HapnetWindow.h:28:0,
                 from gui/HapnetWindow.cpp:52:
seqio/GeoTrait.h:93:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double GeoTrait::SMALL’ of non-integral type [-fpermissive]
   const static double SMALL = 1E-6;
                       ^~~~~
In file included from gui/HapLayer.h:9:0,
                 from gui/MapView.h:11,
                 from gui/HapnetWindow.h:29,
                 from gui/HapnetWindow.cpp:52:
/usr/include/marble/MarbleWidget.h:1138:10: error: ‘void Marble::MarbleWidget::connectNotify(const QMetaMethod&)’ marked ‘override’, but does not override
     void connectNotify(const QMetaMethod &signal) override;
          ^~~~~~~~~~~~~
/usr/include/marble/MarbleWidget.h:1139:10: error: ‘void Marble::MarbleWidget::disconnectNotify(const QMetaMethod&)’ marked ‘override’, but does not override
     void disconnectNotify(const QMetaMethod &signal) override;
          ^~~~~~~~~~~~~~~~
In file included from gui/NetworkModel.h:20:0,
                 from gui/NetworkLayout.h:4,
                 from gui/NetworkView.h:11,
                 from gui/MapView.h:14,
                 from gui/HapnetWindow.h:29,
                 from gui/HapnetWindow.cpp:52:
gui/NetworkItem.h:21:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkItem::VERTWEIGHT’ of non-integral type [-fpermissive]
   static const double VERTWEIGHT = 1;
                       ^~~~~~~~~~
gui/NetworkItem.h:22:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkItem::VERTRAD’ of non-integral type [-fpermissive]
   static const double VERTRAD = 15;
                       ^~~~~~~
gui/NetworkItem.h:23:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkItem::EDGELENGTH’ of non-integral type [-fpermissive]
   static const double EDGELENGTH = 50;
                       ^~~~~~~~~~
In file included from gui/NetworkView.h:11:0,
                 from gui/MapView.h:14,
                 from gui/HapnetWindow.h:29,
                 from gui/HapnetWindow.cpp:52:
gui/NetworkLayout.h:26:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::GOODENOUGH’ of non-integral type [-fpermissive]
   static const double GOODENOUGH = 1E-4;
                       ^~~~~~~~~~
gui/NetworkLayout.h:150:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::VERYSMALL’ of non-integral type [-fpermissive]
   static const double VERYSMALL = 1E-8;
                       ^~~~~~~~~
gui/NetworkLayout.h:151:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::FAIRLYSMALL’ of non-integral type [-fpermissive]
   static const double FAIRLYSMALL = 1E-6;
                       ^~~~~~~~~~~
gui/NetworkLayout.h:152:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::SMALL’ of non-integral type [-fpermissive]
   static const double SMALL = 1E-4;
                       ^~~~~
gui/NetworkLayout.h:157:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::BARNESHUTTHETA’ of non-integral type [-fpermissive]
   static const double BARNESHUTTHETA = 0.7;
                       ^~~~~~~~~~~~~~
gui/NetworkLayout.h:158:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::RESTARTTHRESHOLD’ of non-integral type [-fpermissive]
   static const double RESTARTTHRESHOLD = 0.2;
                       ^~~~~~~~~~~~~~~~
gui/NetworkLayout.h:159:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double NetworkLayout::MAXCOS’ of non-integral type [-fpermissive]
   static const double MAXCOS = 0.5;
                       ^~~~~~
In file included from gui/HapnetWindow.h:32:0,
                 from gui/HapnetWindow.cpp:52:
popgen/Statistics.h:109:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double Statistics::EPS’ of non-integral type [-fpermissive]
   const static double EPS = 3.0e-7;
                       ^~~
popgen/Statistics.h:110:23: warning: ‘constexpr’ needed for in-class initialization of static data member ‘const double Statistics::FPMIN’ of non-integral type [-fpermissive]
   const static double FPMIN = 1.0e-30;
                       ^~~~~
In file included from gui/HapnetWindow.cpp:57:0:
gui/GroupItemDialog.h:157:15: warning: ‘template<class> class std::auto_ptr’ is deprecated [-Wdeprecated-declarations]
   static std::auto_ptr<QIcon> _lockedIcon;// = 0;
               ^~~~~~~~
In file included from /usr/include/c++/7/bits/locale_conv.h:41:0,
                 from /usr/include/c++/7/locale:43,
                 from /usr/include/c++/7/iomanip:43,
                 from gui/HapnetWindow.cpp:44:
/usr/include/c++/7/bits/unique_ptr.h:51:28: note: declared here
   template<typename> class auto_ptr;
                            ^~~~~~~~
Makefile:835: recipe for target 'HapnetWindow.o' failed
make: *** [HapnetWindow.o] Error 1



```

Any thoughts?

---

### Post by jpfontenelle on 2018-10-18
> **norobro said:**
> You're welcome.

It looks like you are missing a few things in your pro file. Here's mine:```
[FONT=monospace][COLOR=#000000]######################################################################[/COLOR]
# Automatically generated by qmake (2.01a) Sat Mar 17 11:24:10 2012
######################################################################

TEMPLATE = app
TARGET = popart
LIBS += -ldl -lcolamd
[COLOR=#FF0000]DEPENDPATH += . gui networks popgen seqio tree  
INCLUDEPATH += . networks seqio popgen tree gui[/COLOR]  
DEFINES += NET_QT QT_DISABLE_DEPRECATED_BEFORE=0x000000
QMAKE_CXXFLAGS += -fpermissive
CONFIG += qt warn_on release
QT += svg widgets core printsupport [COLOR=#FF0000]concurrent[/COLOR]

# default directory for lp_solve headers
##### identical from here to EOF
[/FONT]
```
If making these changes doesn't work please post the error messages you get surrounded buy code tags.


Also, this is my popart.pro now:

```
####################################################################### Automatically generated by qmake (2.01a) Sat Mar 17 11:24:10 2012
######################################################################


TEMPLATE = app
TARGET = popart
LIBS += -ldl -lcolamd
DEPENDPATH += . gui networks popgen seqio tree  
INCLUDEPATH += . networks seqio popgen tree gui  
DEFINES += NET_QT QT_DISABLE_DEPRECATED_BEFORE=0x000000
QMAKE_CXXFLAGS += -fpermissive
CONFIG += qt warn_on release
QT += svg widgets core printsupport concurrent


# default directory for lp_solve headers
unix:!macx{
  PRELPSOLVEDIR=/usr/include/lpsolve
  PREMARBLEDIR=/usr/include/marble


  exists($$PRELPSOLVEDIR/lp_lib.h){
  DEPENDPATH += $$PRELPSOLVEDIR
  INCLUDEPATH += $$PRELPSOLVEDIR
  } else:exists($$LPSOLVEDIR/lp_lib.h ) {
  DEPENDPATH += $$LPSOLVEDIR
  INCLUDEPATH += $$LPSOLVEDIR
      } else {
  error( "lpsolve headers not found!" )
  }


  exists($$PREMARBLEDIR/MarbleWidget.h){
  DEPENDPATH += $$PREMARBLEDIR
  INCLUDEPATH += $$PREMARBLEDIR
  } else:exists($$MARBLEDIR/MarbleWidget.h ) {
  DEPENDPATH += $$MARBLEDIR
  INCLUDEPATH += $$MARBLEDIR
      } else {
  error( "Marble headers not found!" )
  }
  
  LIBS += -L/usr/lib/lp_solve/ -llpsolve55 -lmarblewidget-qt5
  QMAKE_RPATHDIR += /usr/lib/lp_solve/
  #QMAKE_POST_LINK = build_help.sh
}


macx{
  ICON = popart.icns
  INCLUDEPATH += /usr/local/include/lpsolve /usr/local/include/marble
  LIBS += -llpsolve55 -lmarblewidget


  RC_FILE = popart.rc
  QMAKE_MACOSX_DEPLOYMENT_TARGET = 10.6
  QMAKE_MAC_SDK = macosx10.6
}


win32{
  INCLUDEPATH += "c:/lpsolve55" "c:/marble/marble"
  LIBS += "c:/lpsolve55/lpsolve55.lib" "c:/marble/libmarblewidget.dll"
  CONFIG += exceptions rtti #static static-libgcc
  RC_FILE = popart.rc


}


# Input
HEADERS += gui/AlignmentDelegate.h \
           gui/AlignmentModel.h \
           gui/AlignmentView.h \
           gui/Assistant.h \
           gui/BarchartItem.h \
           gui/BorderRectItem.h \
           gui/CitationDialog.h \
           gui/ColourDialog.h \
           gui/ColourTheme.h \
           gui/EdgeItem.h \
           gui/GroupItemDialog.h \
           gui/HapnetWindow.h \
           gui/HapAppError.h \
           gui/HapLayer.h \
           gui/HapLocation.h \
           gui/LabelItem.h \
           gui/LegendItem.h \
           gui/MapLegendDialog.h \
           gui/MapLegendWidget.h \
           gui/MapView.h \
           gui/MonospaceMessageBox.h \
           gui/MoveCommand.h \
           gui/NetworkItem.h \
           gui/NetworkLayout.h \
           gui/NetworkModel.h \
           gui/NetworkScene.h \
           gui/NetworkView.h \
           gui/SelectionRange.h \
           gui/TaxBoxItem.h \
           gui/TraitItem.h \
           gui/TraitModel.h \
           gui/TraitView.h \
           gui/VertexItem.h \
           gui/XPM.h \
           networks/AbstractMSN.h \
           networks/AncestralSeqNet.h \
           networks/ConcreteHapNet.h \
           networks/Edge.h \
           networks/Graph.h \
           networks/HapNet.h \
           networks/IntNJ.h \
           networks/MinSpanNet.h \
           networks/MedJoinNet.h \
           networks/NetworkError.h \
           networks/Vertex.h \
           networks/ParsimonyNet.h \
           networks/TCS.h \
           networks/TightSpanWalker.h \
           popgen/Statistics.h \
           popgen/StatsError.h \
           seqio/GeneticCode.h \
           seqio/GeoTrait.h \
           seqio/NexusParser.h \
           seqio/ParserTools.h \
           seqio/PhylipParser.h \
           seqio/SeqParseError.h \
           seqio/SeqParser.h \
           seqio/Sequence.h \
           seqio/SequenceError.h \
           seqio/TableParser.h \
           seqio/Trait.h \
           tree/ParsimonyNode.h \
           tree/ParsimonyTree.h \
           tree/SeqNode.h \
           tree/SeqTree.h \
           tree/Tree.h \
           tree/TreeError.h \
           tree/TreeNode.h 
SOURCES += gui/AlignmentDelegate.cpp \
           gui/AlignmentModel.cpp \
           gui/AlignmentView.cpp \
           gui/Assistant.cpp \
           gui/BarchartItem.cpp \
           gui/BorderRectItem.cpp \
           gui/CitationDialog.cpp \
           gui/ColourDialog.cpp \
           gui/ColourTheme.cpp \
           gui/EdgeItem.cpp \
           gui/GroupItemDialog.cpp \
           gui/HapnetWindow.cpp \
           gui/HapApp.cpp \
           gui/HapAppError.cpp \
           gui/HapLayer.cpp \
           gui/HapLocation.cpp \
           gui/LabelItem.cpp \
           gui/LegendItem.cpp \
           gui/MapLegendDialog.cpp \
           gui/MapLegendWidget.cpp \
           gui/MapView.cpp \
           gui/MonospaceMessageBox.cpp \
           gui/MoveCommand.cpp \
           gui/NetworkItem.cpp \
           gui/NetworkLayout.cpp \
           gui/NetworkModel.cpp \
           gui/NetworkScene.cpp \
           gui/NetworkView.cpp \
           gui/SelectionRange.cpp \
           gui/TaxBoxItem.cpp \
           gui/TraitItem.cpp \
           gui/TraitModel.cpp \
           gui/TraitView.cpp \
           gui/VertexItem.cpp \
           networks/AbstractMSN.cpp \
           networks/AncestralSeqNet.cpp \
           networks/ConcreteHapNet.cpp \
           networks/Edge.cpp \
           networks/Graph.cpp \
           networks/HapNet.cpp \
           networks/IntNJ.cpp \
           networks/MinSpanNet.cpp \
           networks/MedJoinNet.cpp \
           networks/NetworkError.cpp \
           networks/Vertex.cpp \
           networks/ParsimonyNet.cpp \
           networks/TCS.cpp \
           popgen/Statistics.cpp \
           popgen/StatsError.cpp \
           networks/TightSpanWalker.cpp \
           seqio/GeneticCode.cpp \
           seqio/GeoTrait.cpp \
           seqio/NexusParser.cpp \
           seqio/ParserTools.cpp \
           seqio/PhylipParser.cpp \
           seqio/SeqParseError.cpp \
           seqio/SeqParser.cpp \
           seqio/Sequence.cpp \
           seqio/SequenceError.cpp \
           seqio/TableParser.cpp \
           seqio/Trait.cpp \
           tree/ParsimonyNode.cpp \
           tree/ParsimonyTree.cpp \
           tree/SeqNode.cpp \
           tree/SeqTree.cpp \
           tree/Tree.cpp \
           tree/TreeError.cpp \
           tree/TreeNode.cpp
```

---

### Post by jpfontenelle on 2018-10-18
> **spjackson said:**
> And, of course, you will need to have installed Qt5's development tools & libraries and be using Qt5's qmake.

Hey bud, thanks for the tip.

Correct me if I am wrong, but it seems I don't have Qt5:

```

jpfontenelle@Wallace:~$ qmake -vQMake version 2.01a
Using Qt version 4.8.7 in /usr/lib/x86_64-linux-gnu



```

Is that correct? Or the system is just showing the Qt4?

If I need to get the Qt5, which one should I get? (sorry about theses questions, I am simply completely lost regarding this)

```
jpfontenelle@Wallace:~$ sudo apt-get install qt5qt5-assistant              qt5qevercloud-dev
qt5ct                      qt5-qmake
qt5-default                qt5-qmake-bin
qt5-doc                    qt5-qmltooling-plugins
qt5-doc-html               qt5serialport-examples
qt5dxcb-plugin             qt5-style-kvantum
qt5-gtk-platformtheme      qt5-style-kvantum-l10n
qt5-image-formats-plugins  qt5-style-kvantum-themes
qt5keychain-dev            qt5-style-plugins
jpfontenelle@Wallace:~$ sudo apt-get install qt5



```

---

### Post by jpfontenelle on 2018-10-25
Hello everyone. 

I followed the steps proposed by Norobro and Spjackson.

I downloaded and installed qt5:

jpfontenelle@Wallace:~/Downloads/popart-1.7/src$ qmake -v
QMake version 3.1
Using Qt version 5.9.5 in /usr/lib/x86_64-linux-gnu


And am trying to compile with the alterations in popart.pro as presented previously.

However, it still doesn work:

```

g++ -c -pipe -fpermissive -O2 -Wall -W -D_REENTRANT -fPIC -DNET_QT -DQT_DISABLE_DEPRECATED_BEFORE=0x000000 -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_PRINTSUPPORT_LIB -DQT_WIDGETS_LIB -DQT_GUI_LIB -DQT_CONCURRENT_LIB -DQT_CORE_LIB -I. -I. -Inetworks -Iseqio -Ipopgen -Itree -Igui -isystem /usr/include/lpsolve -isystem /usr/include/marble -isystem /usr/include/x86_64-linux-gnu/qt5 -isystem /usr/include/x86_64-linux-gnu/qt5/QtSvg -isystem /usr/include/x86_64-linux-gnu/qt5/QtPrintSupport -isystem /usr/include/x86_64-linux-gnu/qt5/QtWidgets -isystem /usr/include/x86_64-linux-gnu/qt5/QtGui -isystem /usr/include/x86_64-linux-gnu/qt5/QtConcurrent -isystem /usr/include/x86_64-linux-gnu/qt5/QtCore -I. -isystem /usr/include/libdrm -I/usr/lib/x86_64-linux-gnu/qt5/mkspecs/linux-g++ -o GroupItemDialog.o gui/GroupItemDialog.cpp
In file included from gui/GroupItemDialog.cpp:1:0:
gui/GroupItemDialog.h:157:15: warning: ‘template<class> class std::auto_ptr’ is deprecated [-Wdeprecated-declarations]
   static std::auto_ptr<QIcon> _lockedIcon;// = 0;
               ^~~~~~~~
In file included from /usr/include/c++/7/memory:80:0,
                 from gui/GroupItemDialog.h:24,
                 from gui/GroupItemDialog.cpp:1:
/usr/include/c++/7/bits/unique_ptr.h:51:28: note: declared here
   template<typename> class auto_ptr;
                            ^~~~~~~~
gui/GroupItemDialog.cpp:25:1: warning: ‘template<class> class std::auto_ptr’ is deprecated [-Wdeprecated-declarations]
 auto_ptr<QIcon> GroupedTreeWidgetItem::_lockedIcon(new QIcon);
 ^~~~~~~~
In file included from /usr/include/c++/7/memory:80:0,
                 from gui/GroupItemDialog.h:24,
                 from gui/GroupItemDialog.cpp:1:
/usr/include/c++/7/bits/unique_ptr.h:51:28: note: declared here
   template<typename> class auto_ptr;
                            ^~~~~~~~
gui/GroupItemDialog.cpp: In member function ‘virtual QMimeData* UnsortedListWidget::mimeData(QList<QListWidgetItem*>) const’:
gui/GroupItemDialog.cpp:450:29: error: invalid use of incomplete type ‘class QMimeData’
   QMimeData *mimeData = new QMimeData;
                             ^~~~~~~~~
In file included from /usr/include/x86_64-linux-gnu/qt5/QtGui/QContextMenuEvent:1:0,
                 from gui/GroupItemDialog.h:5,
                 from gui/GroupItemDialog.cpp:1:
/usr/include/x86_64-linux-gnu/qt5/QtGui/qevent.h:596:7: note: forward declaration of ‘class QMimeData’
 class QMimeData;
       ^~~~~~~~~
gui/GroupItemDialog.cpp:451:11: error: invalid use of incomplete type ‘class QMimeData’
   mimeData->setData("text/x-popart-pop", itemData);
           ^~
In file included from /usr/include/x86_64-linux-gnu/qt5/QtGui/QContextMenuEvent:1:0,
                 from gui/GroupItemDialog.h:5,
                 from gui/GroupItemDialog.cpp:1:
/usr/include/x86_64-linux-gnu/qt5/QtGui/qevent.h:596:7: note: forward declaration of ‘class QMimeData’
 class QMimeData;
       ^~~~~~~~~
gui/GroupItemDialog.cpp: In member function ‘virtual QMimeData* GroupedTreeWidget::mimeData(QList<QTreeWidgetItem*>) const’:
gui/GroupItemDialog.cpp:557:29: error: invalid use of incomplete type ‘class QMimeData’
   QMimeData *mimeData = new QMimeData;
                             ^~~~~~~~~
In file included from /usr/include/x86_64-linux-gnu/qt5/QtGui/QContextMenuEvent:1:0,
                 from gui/GroupItemDialog.h:5,
                 from gui/GroupItemDialog.cpp:1:
/usr/include/x86_64-linux-gnu/qt5/QtGui/qevent.h:596:7: note: forward declaration of ‘class QMimeData’
 class QMimeData;
       ^~~~~~~~~
gui/GroupItemDialog.cpp:558:11: error: invalid use of incomplete type ‘class QMimeData’
   mimeData->setData("text/x-popart-pop", itemData);
           ^~
In file included from /usr/include/x86_64-linux-gnu/qt5/QtGui/QContextMenuEvent:1:0,
                 from gui/GroupItemDialog.h:5,
                 from gui/GroupItemDialog.cpp:1:
/usr/include/x86_64-linux-gnu/qt5/QtGui/qevent.h:596:7: note: forward declaration of ‘class QMimeData’
 class QMimeData;
       ^~~~~~~~~
gui/GroupItemDialog.cpp: In member function ‘virtual bool GroupedTreeWidget::dropMimeData(QTreeWidgetItem*, int, const QMimeData*, Qt::DropAction)’:
gui/GroupItemDialog.cpp:567:39: error: invalid use of incomplete type ‘const class QMimeData’
   if (action == Qt::MoveAction && data->hasFormat("text/x-popart-pop"))
                                       ^~
In file included from /usr/include/x86_64-linux-gnu/qt5/QtGui/QContextMenuEvent:1:0,
                 from gui/GroupItemDialog.h:5,
                 from gui/GroupItemDialog.cpp:1:
/usr/include/x86_64-linux-gnu/qt5/QtGui/qevent.h:596:7: note: forward declaration of ‘class QMimeData’
 class QMimeData;
       ^~~~~~~~~
gui/GroupItemDialog.cpp:571:33: error: invalid use of incomplete type ‘const class QMimeData’
       QByteArray itemData = data->data("text/x-popart-pop");
                                 ^~
In file included from /usr/include/x86_64-linux-gnu/qt5/QtGui/QContextMenuEvent:1:0,
                 from gui/GroupItemDialog.h:5,
                 from gui/GroupItemDialog.cpp:1:
/usr/include/x86_64-linux-gnu/qt5/QtGui/qevent.h:596:7: note: forward declaration of ‘class QMimeData’
 class QMimeData;
       ^~~~~~~~~
Makefile:1053: recipe for target 'GroupItemDialog.o' failed
make: *** [GroupItemDialog.o] Error 1



```

Ideas?

Cheers

---

### Post by norobro on 2018-10-25
Did you make the two additional changes at the bottom of post #13?```
src/gui/NetworkView.cpp:7: [COLOR=#ff0000]//#include <QtConcurrentMap>[/COLOR] // comment out this line - removed from Qt5
src/gui/GroupItemDialog.cpp:20: [COLOR=#ff0000]#include <QtCore>[/COLOR] // add this line

```
Including the QtCore header should get rid of the QMimeData error.

---

### Post by jpfontenelle on 2018-10-30
Hello everyone!

Yes, norobro, I have forgotten to comment the src/gui/NetworkView.cpp line... Now it worked! 
So far at least..

Thanks for all the help!!

Cheers

JP

---

