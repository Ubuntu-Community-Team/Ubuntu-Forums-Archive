---
title: "Downloading and installing a program help.. please"
date: 2014-10-30
forum: New to Ubuntu
---

### Post by Marni on 2014-10-30
I've done a whole days work of researching how to install a program on  ubuntu.. so first I downloaded python.. unpackaged it from .tar.xz now  its just python-3.4.2 then I navigated to the dir in terminal.. then ran  the ./configure make make test sudo make install commands which took  like 10 minutes on my ultra fast broadband .. scanning all the files  etc.. now thats all finished how do I open python? it seems like nothing  has changed ? anyone please

---

### Post by grahammechanical on 2014-10-30
As far as I know Python is a programming language. If you have downloaded and compiled Python what you have installed are Python libraries that an application written in Python can use when it is run. This is my understanding.

I also think that Ubuntu already includes a version of Python.

[http://en.wikipedia.org/wiki/Python_(programming_language)](http://en.wikipedia.org/wiki/Python_(programming_language))

My system has Python 3-six installed.

Regards.

---

### Post by Marni on 2014-10-30
Oh thanks i realised i had to download IDLE aswell for python

---

### Post by Impavidus on 2014-10-30
First choice when installing software on Ubuntu is from the official repositories, which can be accessed through software centre, synaptic or terminal. Both python 2.7 and 3.4 are available from the repositories (on Ubuntu 14.04, grahammechanical runs a later version of Ubuntu), including the IDLE IDE for both versions. This is the easiest way of installing (one click basically) and will provide automatic bugfixes. In fact, both versions of python are installed by default, but IDLE is not.

Only if something is not available from the repositories, one would use other forms of installation: PPAs, separate .debs, precompiled binaries, source code. It seems you tried installing from source code, which is the hardest way to install something on Ubuntu.

---

### Post by Penguin360 on 2014-10-30
What program are you trying to install?

---

