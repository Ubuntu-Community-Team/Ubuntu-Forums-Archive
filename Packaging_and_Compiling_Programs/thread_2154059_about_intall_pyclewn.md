---
title: "about intall pyclewn"
date: 2013-06-13
forum: Packaging and Compiling Programs
---

### Post by genime on 2013-06-13
Hi,

when I  find a excellent debugger in vim, finally I chose pyclewn, so I downloaded the pyclewn-1.10.py3.tar.gz file from [http://sourceforge.net/projects/pyclewn/](http://sourceforge.net/projects/pyclewn/)   , I issue the following command:

[COLOR=#000000][FONT=Consolas]vimdir=$HOME/.vim python setup.py install --force --home=$HOME

then the error message is&#65306;&#12288;This vesion of pyclewn does not support Python 2.

however my pc environmnet is ubuntu13.04 
and 
$python --version
Python 2.7.4

But in pyclewn official site, I found pylewn supported python 2 & 3, what's happened? I'm confused.

Can anyone give a suggestion? Many thanks!
[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]
[/FONT][/COLOR]

---

### Post by steeldriver on 2013-06-13
I'm not familiar with pyclewn, but it looks like you would need pyclewn-1.10.**py2**.tar.gz to run on a system that uses Python 2.x as the default - although pyclewn supports both Python 2 and Python 3, it does so using separate tarballs

---

### Post by genime on 2013-06-13
> **steeldriver said:**
> I'm not familiar with pyclewn, but it looks like you would need pyclewn-1.10.**py2**.tar.gz to run on a system that uses Python 2.x as the default - although pyclewn supports both Python 2 and Python 3, it does so using separate tarballs

thanks,  that's the problem.  howerver, I use the wrong tarball.

---

