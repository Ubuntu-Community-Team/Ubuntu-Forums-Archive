---
title: "Broken Packages error while Intsalling Pygame for Python 3.2"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by touches on 2012-10-24
I have python 2.7 and python 3.2 . Before reinstalling python 3.2 from the repo's i had the pygame 1.9.1 installed from pygame's site and it worked well on Python 2.7. I had to remove my original python 3.2 and had it re-installed from Ubuntu's repo's. Now when i try to import pygame in both of my versions of python i get the 

```
>>> import python
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named python
```How do i fix this??
 and when i try to install Pygame for Python 3.2 by following the steps given in this site
[http://pythonfun.wordpress.com/2011/08/08/installing-pygame-with-python-3-2-on-ubuntu-11-04/](http://pythonfun.wordpress.com/2011/08/08/installing-pygame-with-python-3-2-on-ubuntu-11-04/)

When i give this command:
```
sudo apt-get install python3-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev libsmpeg-dev python-numpy subversion libportmidi-dev
```I get this error
```
libsdl1.2-dev is already the newest version.
libsdl1.2-dev set to manually installed.
libportmidi-dev is already the newest version.
libsdl-image1.2-dev is already the newest version.
libsdl-mixer1.2-dev is already the newest version.
libsdl-ttf2.0-dev is already the newest version.
libsmpeg-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python-numpy : Depends: python (< 2.8) but 3.2-1 is to be installed
E: Unable to correct problems, you have held broken packages.
```How do i correct this?? Please help me out

---

### Post by Bashing-om on 2012-10-25
Hi touches.

My suggestion is to remove both the python packages, and then install python3.2 again.

Be advised all I find in the repositories is the developer package for 3.2.
terminal codes:
```
sudo apt-get remove --purge python
sudo apt-get remove --purge python3.2-dev
```[INDENT][INDENT]hth <==BDQ

[/INDENT][/INDENT]

---

### Post by touches on 2012-10-26
@[Bashing-om]("http://ubuntuforums.org/member.php?u=1111508")
Thanks for the handy command tips, besides having this broken packages i totally messed up my Ubuntu 11.10 with many of the features missing. So following Nikth's advice i have now upgraded to Ubuntu 12.04

---

### Post by Bashing-om on 2012-10-26
hey ...Good move....LTS good till '17 !

[INDENT]happy ubuntu'n <== BDQ

[/INDENT]

---

