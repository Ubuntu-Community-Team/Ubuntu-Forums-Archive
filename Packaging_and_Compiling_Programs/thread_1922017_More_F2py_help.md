---
title: "More F2py help"
date: 2012-02-07
forum: Packaging and Compiling Programs
---

### Post by brushman on 2012-02-07
I'm following the users guide here (see '2.1 The quick way'):
[http://cens.ioc.ee/projects/f2py2e/usersguide/index.html#three-ways-to-wrap-getting-started](http://cens.ioc.ee/projects/f2py2e/usersguide/index.html#three-ways-to-wrap-getting-started)
And this guide here (see '3. Converting the Fortran to a shared library'):
[http://moo.nac.uci.edu/~hjm/fd_rrt1d/index.html]("http://moo.nac.uci.edu/%7Ehjm/fd_rrt1d/index.html")

Note that these outline essentially the same steps, except the second link specifies that you must change the main program to a subroutine in the FORTRAN code and pass the input as parameters, all of which I have done.

Anyways, here's the command I enter, and the output is attached (broken into 2 files because it is long and exceeded upload limit):
f2py -c *.f -m slab 2>&1 | tee outputfile.txt

Ideally this would make a module which I could import to python and call the program from python.

Admittedly I don't really know what I'm doing, so any advice on how I can move forward with this would be great.

---

