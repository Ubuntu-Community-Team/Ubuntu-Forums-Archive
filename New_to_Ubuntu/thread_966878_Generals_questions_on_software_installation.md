---
title: "Generals questions on software installation"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2008-11-01
Hi
I installed python using this command :
apt-get install python

I installed python-pygame using this command :
apt-get install python-pygame

I then installed pgSlidesShow tarball using this command :
tar -zxvf pgSlidesShow 
in folder /Sources/pgSlidesShow/ 

All installation looked fine.
When I try to start pgSlideShow, it tells me python-pygame is not installed

Questions :
How can I verified that all the software are correctly installed ?
When using commands : apt-get install, were is software installed (what path) ?
When installing software with tar, can I install them anywhere ?

Thanks,

PL

---

### Post by Pierrot Lafouine on 2008-11-01
.

---

### Post by petronell on 2008-11-01
when you entered the install commands into terminal did you use sudo?

if you did not this would explain why the software is not installed?

can you check synaptic to see if the packages are installed there? go to system then administration then select synaptic package manager.

if you did not use sudo re-type the same commands in terminal but head them with sudo (this executes them as root).

daveR

---

### Post by Teabicky on 2008-11-01
Try using the "find" or "locate" commands in Terminal to locate the programs eg. > locate python-pygame, "locate" is quicker and better than "find" but if "locate" does not find it then "find" probably should.

You could also try the gksudo command to start the file in the GUI eg. > gksudo python-pygame.

---

### Post by Pierrot Lafouine on 2008-11-01
Hi.
I locate all software
And yes, I used sudo before installing software
What do I do next ?

---

### Post by Teabicky on 2008-11-01
Have you tries the "gksudo" command to start the program up?

---

### Post by Pierrot Lafouine on 2008-11-02
HiI have done everything you asked me, without success.
Programs seams to be installed, how do I make sure they start correctly ?
Anyway to see running programs/processes like under Windoz ?

Thanks

---

### Post by montun on 2008-11-02
Hi hope this helps

The following should get pgSlideShow to work

```

sudo apt-get install python-pygame
cd $HOME
mkdir pygames
cd pygames
wget http://www.bradmontgomery.net/pgSlideShow/pgSlideShow.tar.gz
tar -zxvf pgSlideShow.tar.gz
cd pgSlideShow
python pgSlideShow.py <Your image directory>

```

To see running programs on your PC, run top (press h for help). To see what is started in current terminal run ps.

---

### Post by Pierrot Lafouine on 2008-11-02
Thanks,
This is the output of the code you propose me :

Traceback (most recent call last):
  File "pgSlideShow.py", line 17, in <module>
    import pygame
ImportError: No module named pygame

What do i do next ?

---

### Post by montun on 2008-11-02
post the output of "dpkg-query --status python-pygame", "env" and 
```

python
>>> import sys
>>> sys.path

```

---

### Post by Pierrot Lafouine on 2008-11-02
The output of : dpkg-query --status python-pygame

Package: python-pygame
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 2464
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: pygame
Version: 1.7.1release-4.1ubuntu1
Replaces: python2.3-pygame, python2.4-pygame
Provides: python2.4-pygame, python2.5-pygame
Depends: python-central (>= 0.5.8), python (<< 2.6), python (>= 2.4), libc6 (>= 2.6-1), libsdl-image1.2 (>= 1.2.5), libsdl-mixer1.2 (>= 1.2.6), libsdl-ttf2.0-0, libsdl1.2debian (>= 1.2.10-1), libsmpeg0, python-numeric (>= 24.2-3)
Conflicts: python2.3-pygame, python2.4-pygame
Description: SDL bindings for games development in Python
 A multimedia development kit for Python. Pygame provides modules for you
 to access the video display, play sounds, track time, read the mouse and
 joystick, control the CD player, render true type fonts and more. It does
 this using mainly the cross-platform SDL library, a lightweight wrapper
 to OS-specific APIs.
 .
 This package also includes Pygame's API documentation and examples.
Original-Maintainer: Ed Boraas <ed@debian.org>
Python-Version: 2.4, 2.5

---

### Post by Pierrot Lafouine on 2008-11-02
.

---

### Post by Pierrot Lafouine on 2008-11-02
How do I solve conflict ?
*> Conflicts: python2.3-pygame, python2.4-pygame

---

### Post by Pierrot Lafouine on 2008-11-02
up

---

### Post by Pierrot Lafouine on 2008-11-02
I remove python-pygame and re-install it,
I still have same results
What do i do next ?

---

### Post by Pierrot Lafouine on 2008-11-02
Any ideas ???

---

### Post by Pierrot Lafouine on 2008-11-02
:(

---

### Post by handydan918 on 2008-11-02
> **Pierrot Lafouine said:**
> HiI have done everything you asked me, without success.
Programs seams to be installed, how do I make sure they start correctly ?
Anyway to see running programs/processes like under Windoz ?

Thanks
Yep. Try ```
top
```or```
ps aux
```

---

### Post by montun on 2008-11-03
Sorry I updated my previous post on page one to
> **montun said:**
> post the output of "dpkg-query --status python-pygame", "env" and 
```

python
>>> import sys
>>> sys.path

```
We need to check that the python search path includes the pygames libs on your PC

---

### Post by montun on 2008-11-03
In the Python console you could also try to post the output of 
```

>>> import pygame

```

---

### Post by montun on 2008-11-03
What I was looking for in the 'dpkg-query --status python-pygame' was the version you had installed and the status, which was "install ok installed". So everything is fine with that package.

Try to run python in the terminal (as a normal user) and the execute the following commands in the resulting python shell, and post the output here.
```

python
>>> import sys
>>> sys.path
.
.
.
>>> import pygame

```

---

### Post by Pierrot Lafouine on 2008-11-07
Python path seam to be the problem, not the installation
I tried in Python console :
```
*>>>>import pygame
```
and get this error message :

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named pygame

Were are python path lacated ?

Thanks

---

### Post by Pierrot Lafouine on 2008-11-07
any idea wher I can find and change Python path  ?

---

### Post by Pierrot Lafouine on 2008-11-07
up

---

### Post by Pierrot Lafouine on 2008-11-08
Hi
Where are located path file for Python ?
They are so much installed with Python !!!

Thanks!

---

### Post by Pierrot Lafouine on 2008-11-08
I want to have Python and Pygame working on my computer.
I'm I asking this in good forum ?
:confused::confused::confused:
I'm Linux absolute beginner
:(:(:(

---

