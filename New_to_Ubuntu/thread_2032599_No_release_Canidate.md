---
title: "No release Canidate"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-07-24
Im trying to install some python packages in regards to learning python.

The book came with an ubuntu installer (install.sh), which I ran:
```

glenn@design:~/book/hello_world$ chmod a+x install.sh
glenn@design:~/book/hello_world$ ls -al
total 28
drwxr-xr-x  4 glenn glenn  4096 Jun 17  2009 .
drwxrwxr-x  3 glenn glenn  4096 Jul 25 01:40 ..
drwxr-xr-x  4 glenn glenn  4096 Jun 17  2009 easygui
drwxr-xr-x 10 glenn glenn 12288 Jun 17  2009 examples
-rwxr-xr-x  1 glenn glenn   353 Jun 17  2009 install.sh
glenn@design:~/book/hello_world$ sudo ./install.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-numeric is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-numeric' has no installation candidate
glenn@design:~/book/hello_world$ 

```
But It came up with the error:

```

Package python-numeric is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'python-numeric' has no installation candidate

```

Can someone tell me what that means please.

---

### Post by Frogs Hair on 2012-07-24
The first output indicates 2009 packages so, they may be obsolete as the error message indicates. The massage also says the package has been renamed. you could check their website for more information but I only see the latest release.

---

### Post by audiomick on 2012-07-24
My guess is that the script is a couple of years old and is pointing to a package or source that is no longer there.

Why not have a look in the script (open it with an editor) at what it is trying to do and see if you can't install the packages it wants, or the latest versions thereof, via the software centre or the synaptic package manager (which you will have to install first. It is not on 12.04 by default.)

Any rate, I can see the package "python numeric" in both my software centre and my synaptic on this Ubuntu 10.10 install.

---

### Post by Senior_Buckethead on 2012-07-24
I should have put this up first. Here is the script:
```

#!/bin/bash
#standard python packages
apt-get install python-numeric python-pygame python-pythoncard python-wxgtk2.8 spe

#So uh, where is python anyway?
export sitelib=`python -c "from distutils.sysconfig import get_python_lib; print get_python_lib()"`

#easygui
cp easygui/easygui.py $sitelib/easygui.py
cp -R easygui $sitelib/easygui
rm -Rf easygui

```

Now I have had a look in Synaptic, and I have all the standard packages installed except python-numeric.
It might well be obsolete, if so, is there a successor package?
Im running Ubuntu 12.04.

---

### Post by Bufeu on 2012-07-24
> **Senior_Buckethead said:**
> I should have put this up first. Here is the script:
```

#!/bin/bash
#standard python packages
apt-get install python-numeric python-pygame python-pythoncard python-wxgtk2.8 spe

#So uh, where is python anyway?
export sitelib=`python -c "from distutils.sysconfig import get_python_lib; print get_python_lib()"`

#easygui
cp easygui/easygui.py $sitelib/easygui.py
cp -R easygui $sitelib/easygui
rm -Rf easygui

```Now I have had a look in Synaptic, and I have all the standard packages installed except python-numeric.
It might well be obsolete, if so, is there a successor package?
Im running Ubuntu 12.04.I found *python-numpy*.[QUOTE=https://apps.ubuntu.com/cat/applications/python-numpy/]Numpy contains a powerful N-dimensional array object, sophisticated
(broadcasting) functions, tools for integrating C/C++ and Fortran
code, and useful linear algebra, Fourier transform, and random number
capabilities.

[B]Numpy replaces the python-numeric and python-numarray modules which are
now deprecated and shouldn't be used except to support older
software.[/B][/QUOTE]Should be installed by defualt, otherwise run:```
sudo apt-get install python-numpy
```

---

### Post by audiomick on 2012-07-24
Results of an internet search-

[http://sourceforge.net/projects/numpy/]("http://sourceforge.net/projects/numpy/")

[http://numpy.scipy.org/]("http://numpy.scipy.org/")

Before you try and install anything from outside, do some more searching in synaptic for the stuff on those pages. Chances are, it is all there somewhere.

---

### Post by Senior_Buckethead on 2012-07-24
Turns out Ive got numpy
```

glenn@design:~$ sudo apt-get install python-numpy
[sudo] password for glenn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-numpy is already the newest version.
python-numpy set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
glenn@design:~$ 

```

So do you reckon I could just rem out the apt-get line from the script and run it?

---

### Post by Bufeu on 2012-07-24
> **Senior_Buckethead said:**
> Turns out Ive got numpy
```

glenn@design:~$ sudo apt-get install python-numpy
[sudo] password for glenn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-numpy is already the newest version.
python-numpy set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
glenn@design:~$ 

```So do you reckon I could just rem out the apt-get line from the script and run it?Yeah, you can always try. I'd do that.

---

### Post by Senior_Buckethead on 2012-07-24
Works. Thanks Guys.

[SOLVED]

---

### Post by audiomick on 2012-07-24
Great. Have fun with python. ;)

---

