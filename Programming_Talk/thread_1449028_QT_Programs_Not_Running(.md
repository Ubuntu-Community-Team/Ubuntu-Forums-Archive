---
title: "QT Programs Not Running:("
date: 2010-04-07
forum: Programming Talk
---

### Post by nbulchandani on 2010-04-07
[INDENT] 					Hello,
Just Installed Qt once again due to some problems on ubuntu 9.10.no program running now...chcek these details
Application output:
&"warning: GDB: Failed to set controlling terminal: Invalid argument\n"
/bin/bash: /media/sda6/Qt/bin/chapter01/helloWorld: Permission denied
/bin/bash: /media/sda6/Qt/bin/chapter01/helloWorld: Success
Compile Output:
Running build steps for project helloWorld...
Starting: /usr/bin/qmake-qt4 /media/sda6/Qt/examples/chapter01/helloWorld/helloWorld.pro -spec /usr/share/qt4/mkspecs/linux-g++ -r CONFIG+=debug 
Exited with code 0.
Starting: /usr/bin/make -w 
make: Entering directory `/media/sda6/Qt/examples/chapter01/helloWorld'
make: Nothing to be done for `first'.
make: Leaving directory `/media/sda6/Qt/examples/chapter01/helloWorld'
Exited with code 0.
Thanks 				[/INDENT]

---

### Post by Zugzwang on 2010-04-08
Please compile & run the program from the terminal. Perhaps in your case, running will be sufficient. As always when using IDEs in Linux, if you have any problems, this is the first thing to try as almost no one knows all the details about all the IDEs here, which can have influence on the problem you are having.

For compiling, in your case it should be sufficient to go into the directory "/media/sda6/Qt/examples/chapter01/helloWorld" and run "make clean" and finally "make" (since QMake has already been run). Then execute your program using "./<yourprogramname>".

If you then still have problems, please copy&paste the commands you are executing and the error messages you get.

---

