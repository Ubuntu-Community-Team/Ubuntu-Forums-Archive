---
title: "[SOLVED] Python help: extending with C / Where is Python.h?"
date: 2007-07-09
forum: Programming Talk
---

### Post by BeardlessForeigner on 2007-07-09
I am trying to figure out how to extend Python with C using SWIG. I am following the SWIG tutorial here: [http://www.swig.org/tutorial.html]("http://www.swig.org/tutorial.html"), or alternatively the one at the bottom here [http://en.wikibooks.org/wiki/Python_Programming/Extending_with_C]("http://en.wikibooks.org/wiki/Python_Programming/Extending_with_C"). However, once I get to the step 
```
gcc -fpic -c hellomodule.c hello_wrap.c -I/usr/include/python2.5/
```
I'm stuck, the first error being "hello_wrap.c:112:20: error: Python.h: No such file or directory". I've searched my comp and Python.h does not seem to be anywhere so I'm not even sure which directory to point to, yet all the documentation on the Python site and elsewhere seems to assume that it exists and is fine. I guess I'm going to try dling Python's source and looking in there, but it just seemed odd to me and i was wondering if anyone who has successfully done this can explain why i wouldn't have Python.h

---

### Post by BeardlessForeigner on 2007-07-09
Problem solved, that was a quick one I know. I just hadn't realized that by default only part of Python is installed, and I needed to install the python-dev package which includes all the header files.

---

### Post by vyomhere on 2009-02-08
hi friend,
Thanks a lot,
I came across the same problem 
> Python.h: No such file or directory


I was trying to compile sphinx.

Thanks a lot for ur solution.

---

### Post by bmcage on 2009-03-09
Same here, Google is such a nice guy to link you :-)

---

### Post by ninjasmith on 2009-06-06
Yeeeees what a result that fixed it for me too.  good work dude.  just goes to show you should always post the solution to your own problems.  helps everyone out

---

### Post by amol_ko on 2009-06-11
hi all,
can anybody please tell from where this python - dev module be install for windows?
i have installed python and vc++ on my machine...
link for that will be more helpfull...
Thanks in advance...

---

### Post by Zugzwang on 2009-06-11
> **amol_ko said:**
> i have installed python and vc++ on my machine...


The windows installers come without source code. You will probably need to download the sources from the python web site separately.

---

### Post by amol_ko on 2009-06-12
As i am new to python...
on the python site there are lots of different options are there...
i will be thankful if somebody directly provide me the link....
thnaks...

---

### Post by kainlite on 2009-12-26
> **bmcage said:**
> Same here, Google is such a nice guy to link you :-)


Totally agree! :)

---

### Post by roozbeh.daneshvar on 2010-01-27
Thanks a lot for sharing the solution!

---

### Post by FlameFame on 2010-06-03
I've encountered the same problem, googled it, found this topic and thought "Yes! Found the solution!" but bummer, everything remained the same... To go into detailed, I've written
```
sudo apt-get install python2.6-dev
```because when I enter into Python (with python command) it says I'm using Python 2.6.5. Afterwards I've written (note that examples are copied from SWIG, so there shouldn't be any errors in the code)
```
gcc -c -fpic example.c example_wrap.c -I/usr/local/include/python2.6
```and got myself few screens of errors... I cannot seem to make it all work, nor do I know how. Any kind of help would be greatly appreciated :)


P.S. I'm fresh new to both Python and Ubuntu and Linux in general. I'm not a Windows fan-boy, but I am a Windows user.

---

### Post by sukhdeepsingh on 2010-06-30
Hi,
I have python-dev installed but still the problem exists, when i try to execute the program.
Simple program for testing
```
 
#include <stdio.h>
#include <Python.h>
int main() 
{
  printf("Hello, world\n");
  return 0;
}

```

'Python.h: No such file or directory'

I am using Ubuntu 10.04, please help I am looking for the solution from past 2 weeks but no answer present on the web.

Thanks a lot people.
Sukhi

---

### Post by matja on 2010-06-30
Hi,

Assuming *python-dev* is installed, you can use *python-config* to be sure you get the right include directories. An example would be
```

gcc -c -fpic $(python-config --includes) example.c example_wrap.c

```
This should fix the problem that Python.h is not found.

Regards,
Mattias

---

### Post by Malchuth on 2011-03-05
Thanks man, I tried to install numpy for python 3.1 (which is possible by now) but didn't think of installing python3.1-dev instead of python-dev or python2.6-dev. So if anyone else has issues with python3.1 think of modifying the needed package.

---

### Post by ibozzie on 2011-04-28
Thanks so much! I had the same problem - headers not found even with the dev packages installed, and $(python-config --includes) fixed it right up.

---

### Post by Piscanerian on 2011-05-29
I think this is the fastest I've ever found a solution to a linux problem.  

sudo apt-get install python-dev

and voila!  all done.  

Thank you for the help

---

### Post by Sepero on 2011-09-27
#include <python2.6/Python.h>
#include <python2.6/Python.h>
#include <python2.6/Python.h>
#include <python2.6/Python.h>
#include <python2.6/Python.h>

That solved my problem (instead of using #include <Python.h>)

---

### Post by alpsayin on 2011-10-27
> **bmcage said:**
> Same here, Google is such a nice guy to link you :-)

same here, was trying to install tinyos, thank you. :)

---

### Post by Bllz on 2012-04-28
> **Sepero said:**
> #include <python2.6/Python.h>
#include <python2.6/Python.h>
#include <python2.6/Python.h>
#include <python2.6/Python.h>
#include <python2.6/Python.h>

That solved my problem (instead of using #include <Python.h>)

Although this thread seems to be dead, I thought I'd confirm that this fixes the problem.

If you have python-dev installed and you're still getting errors, this method is likely to work.  Be sure to replace python2.6 with your version of python (which should be 2.7 for most people by now).

---

