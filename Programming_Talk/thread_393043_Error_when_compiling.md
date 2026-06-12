---
title: "Error when compiling"
date: 2007-03-25
forum: Programming Talk
---

### Post by Ne0z on 2007-03-25
Hi guys,

i had an error when compiling using make and i am not sure what is the problem .
This was the error msg :

> make -C src bin
make[1]: Entering directory `/home/myname/msl-refbox/src'
/usr/bin/uic -o CardDialog.qt.h CardDialog.ui
/usr/bin/uic -i CardDialog.qt.h -o CardDialog.qt.cpp CardDialog.ui
/usr/bin/moc CardDialog.qt.h >> CardDialog.qt.cpp
/usr/bin/uic -o GoalDialog.qt.h GoalDialog.ui
/usr/bin/uic -i GoalDialog.qt.h -o GoalDialog.qt.cpp GoalDialog.ui
/usr/bin/moc GoalDialog.qt.h >> GoalDialog.qt.cpp
/usr/bin/uic -o CorrectionDialog.qt.h CorrectionDialog.ui
/usr/bin/uic -i CorrectionDialog.qt.h -o CorrectionDialog.qt.cpp CorrectionDialog.ui
/usr/bin/moc CorrectionDialog.qt.h >> CorrectionDialog.qt.cpp
/usr/bin/uic -o RefboxGUI.qt.h RefboxGUI.ui
/usr/bin/uic -i RefboxGUI.qt.h -o RefboxGUI.qt.cpp RefboxGUI.ui
/usr/bin/moc RefboxGUI.qt.h >> RefboxGUI.qt.cpp
CardDialog.qt.cpp:162:2: error: #error "This file was generated using the moc from 3.3.6. It"
CardDialog.qt.cpp:163:2: error: #error "cannot be used with the include files from this version of Qt."
CardDialog.qt.cpp:164:2: error: #error "(The moc has changed too much.)"
make[1]: *** [CardDialog.qt.d] Error 1
make[1]: Leaving directory `/home/myname/msl-refbox/src'
make: *** [bin] Error 2


any idea how can i fix it ?
it ran on my fedora but it didn't on ubuntu. 

thanks guys.

---

### Post by Mirrorball on 2007-03-25
My guess is that it needs Qt 3 and Ubuntu has Qt 4.

---

