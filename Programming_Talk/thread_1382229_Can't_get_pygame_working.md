---
title: "Can't get pygame working"
date: 2010-01-15
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2010-01-15
So I'm learning python from the Head First series by O'Reilly (a great series for any one wanting to learn how to program in most any langauge), and we need the pygame library to do our GUI stuff.  I ran ```
 sudo apt-get install python-pygame
``` and it accomplished successfully, how ever I keep getting errors that there is no module named pygame.  Am I missing something here?

---

### Post by Can+~ on 2010-01-15
Which version of python are you using?

```
~$**apt-cache show python-pygame**
Package: python-pygame
Priority: optional
Section: universe/python
Installed-Size: 4332
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Ed Boraas <ed@debian.org>
Architecture: amd64
Source: pygame
Version: 1.8.1release-1ubuntu1
Replaces: python2.3-pygame, python2.4-pygame
Provides: python2.5-pygame, python2.6-pygame
Depends: python (<< 2.7), python (>= 2.5),
```

The version in the repository works for python 2.x, not sure if you can run pygame with python 3.

---

### Post by c0mput3r_n3rD on 2010-01-15
I'm using python3

---

### Post by Can+~ on 2010-01-15
> **c0mput3r_n3rD said:**
> I'm using python3

I'm not sure if the pygame guys have ported to python3 yet (and their site is down, so I can't check), so you're better off using python2.6 which comes with ubuntu. Python3 is kinda new, and lacks support of 3rd party libraries.

---

### Post by c0mput3r_n3rD on 2010-01-15
And that's what I'm finding while looking around for the answer, except the book I'm reading is only on Python3, and they're saying to use pygame.  I believe that other versions are fairly different as well, as trying to run most of my simple python programs get errors with the built in version of python which I'm assuming to be 2.6?

---

### Post by Can+~ on 2010-01-15
> **c0mput3r_n3rD said:**
> And that's what I'm finding while looking around for the answer, except the book I'm reading is only on Python3, and they're saying to use pygame.  I believe that other versions are fairly different as well, as trying to run most of my simple python programs get errors with the built in version of python which I'm assuming to be 2.6?

There are subtle differences between the syntax in python2.6 to 3. The most obvious ones are the print statement becoming a function, that things like "xrange()" became "range()" (and the older range died), and "raw_input()" became "input()" (again, the original input() died).

Wait for the site to come back and check if they have a debian package for python3. I've been reading that pygame has python3 support, so it's a matter of finding the right package or source code.

---

### Post by c0mput3r_n3rD on 2010-01-15
Alright thanks.  And that would explain the error messages on my simple print and input!

---

