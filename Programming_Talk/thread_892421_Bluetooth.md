---
title: "Bluetooth"
date: 2008-08-17
forum: Programming Talk
---

### Post by praveengsct on 2008-08-17
hi,

    i am a beginner in python programming. anyway i have to run a program which pushes file to bluetooth devices.i have three libraries pybluez,openobex and ussppush. But when i run the main program ,errors show that the files in the libraries which used in the main program cant loaded. where should i paste the library folders in the program. please help me

                                    Thanking you
                                    Praveen

---

### Post by aloshbennett on 2008-08-18
The libraries should be added to your "sys.path"

> $ python
Python 2.2 (#11, Oct  3 2002, 13:31:27)
[GCC 2.96 20000731 (Red Hat Linux 7.3 2.96-112)] on linux2
Type ``help'', ``copyright'', ``credits'' or ``license'' for more information.
>>> import sys
>>> sys.path
['', '/usr/local/lib/python2.3', '/usr/local/lib/python2.3/plat-linux2', 
 '/usr/local/lib/python2.3/lib-tk', '/usr/local/lib/python2.3/lib-dynload', 
 '/usr/local/lib/python2.3/site-packages']
>>>


You could either put your libraries into one of the directories present in the path or add your directory containing the libraries to the path.

[http://docs.python.org/inst/search-path.html#SECTION000410000000000000000](http://docs.python.org/inst/search-path.html#SECTION000410000000000000000)

---

