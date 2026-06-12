---
title: "Howto: Fix PyPanel in Edgy"
date: 2006-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by fuscia on 2006-12-29
this solution was posted by K.Mandla in the *random openbox chatter* thread - [http://ubuntuforums.org/showthread.php?t=190476](http://ubuntuforums.org/showthread.php?t=190476)

it was originally posted by a dr.zombo on K.Mandla's blog (this is already starting to sound like one of those 'latest news on e17' threads. "oh, it was going great for about 20 minutes, last thursday."). anyway, here's that original quote...

[quote=dr.zombo]I got the same problem with pypanel for the last 2 hours, but then I did the following trick:
 
 do an apt-get remove python-xlib
 
 clear all dependencies for python-xlib:
 
 apt-get install debhelper python-dev python-xlib libx11-dev libxft-dev libxpm-dev libimlib2-dev dpatch sed python-central
 
 grab it from here:
 [http://sourceforge.net/projects/python-xlib/](http://sourceforge.net/projects/python-xlib/)
 unpack, and install it with python setup.py install
 
 and finaly cd to pypanel and python setup.py install
 taddaaa it works!!
 
 cheers, dr.zombo[/quote]

of course, you must do *sudo apt-get remove python-xlib*.

i don't know what he meant by "clear all dependencies for python-xlib". this must have happened automatically, somehow, as i didn't do it.

worked for me.

---

### Post by K.Mandla on 2006-12-29
Since I'm a co-conspirator ... yes, it worked for me as well. However, not without also downloading the source for PyPanel and installing that via *sudo python setup.py install* as well. 

So in short: I removed python-xlib and pypanel from the repositories with

```
sudo apt-get remove python-xlib pypanel
```
Then I installed the packages listed above, with the exception of python-xlib (?!) and sed (which is part of ubuntu-minimal ... again: ?!) with

```
sudo aptitude install debhelper python-dev libx11-dev libxft-dev libxpm-dev libimlib2-dev dpatch python-central
```

Then download the python-xlib tarball from [http://sourceforge.net/projects/python-xlib/]("http://sourceforge.net/projects/python-xlib/") and the PyPanel tarball from [http://sourceforge.net/projects/pypanel/]("http://sourceforge.net/projects/pypanel/"). Decompress both.

First move into the python-xlib folder and install with *sudo python setup.py install*. Then jump to the PyPanel folder and install it as well with *sudo python setup.py install*.

Now, when you enter the command *pypanel &* in a terminal window or from within your .xinitrc file, the panel should start.

Not bad for a random blog comment. :-?

---

### Post by apoth on 2007-02-10
Thanks, I followed K.Mandla's comments and it worked a treat.

---

### Post by fobnicat on 2007-04-11
I followed these directions..b ut now when i go into terminal and enter

```
fobnicat@fobnicat-desktop:~$ pypanel
```

my whole computer goes crazy 100% CPU and the new pypanel toolbar is blinking

any help?

---

### Post by dbbolton on 2007-04-28
>   and finaly cd to pypanel
> Then jump to the PyPanel folder

where is this folder exactly ?

---

### Post by regomodo on 2007-09-07
cheers for the tip k.mandla. Pypanel refused to work for me in feisty

---

