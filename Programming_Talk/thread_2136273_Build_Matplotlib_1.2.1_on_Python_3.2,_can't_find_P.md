---
title: "Build Matplotlib 1.2.1 on Python 3.2, can't find Python.h?"
date: 2013-04-17
forum: Programming Talk
---

### Post by ladasky on 2013-04-17
I've gotten out a bit ahead of the standard repositories. I want to use Matplotlib with Python 3, and that means that I need Matplotlib 1.2.1. 

I've done manual builds before. In fact, I did a manual build of Matplotlib 1.0 about two years ago, when it was new.  I always get error messages when I'm doing manual builds.  I do a little Internet searching, and deduce which package contains the file that the error message says is missing.  (Is there a better way?  You can't use **apt-get build-dep** unless you have an **apt** repository, right?).  

Anyway, I got an error message after executing **python setup.py build** in the maplotlib 1.2.1 directory.  Just the tail end is shown:

```
[...]
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -fPIC -DPY_ARRAY_UNIQUE_SYMBOL=MPL_ARRAY_API -DPYCXX_ISO_CPP_LIB=1 -I/usr/local/include -I/usr/include -I/usr/lib/python2.7/dist-packages/numpy/core/include -I/usr/local/include -I/usr/include -I. -I/usr/local/include/freetype2 -I/usr/include/freetype2 -I/usr/lib/python2.7/dist-packages/numpy/core/include/freetype2 -I/usr/local/include/freetype2 -I/usr/include/freetype2 -I./freetype2 -I/usr/include/python2.7 -c src/ft2font.cpp -o build/temp.linux-x86_64-2.7/src/ft2font.o
In file included from ./CXX/Extensions.hxx:37:0,
                 from src/ft2font.h:6,
                 from src/ft2font.cpp:3:
./CXX/WrapPython.h:58:20: fatal error: Python.h: No such file or directory
compilation terminated.
error: command 'gcc' failed with exit status 1
```

I actually remembered this error message from a few years back, and knew that I needed the **python-dev** package.  More specifically, I now need **python3-dev**.  So I downloaded it, and tried my build again.  The error message did not change.

Next I tried **sudo find / -name "Python.h"**. I do indeed have a file named Python.h, in the directory **/usr/include/python3.2mu/**.  So, why isn't **gcc** seeing it?

What is the python3.2mu directory anyway?  Why isn't the directory simply python3.2?  Do I need to add this python3.2mu directory manually to some search path?

Puzzled...

---

### Post by ladasky on 2013-04-17
Quick followup:

> **ladasky said:**
> (Is there a better way?  You can't use **apt-get build-dep** unless you have an **apt** repository, right?).  


Just to see what I would get, I tried executing **sudo apt-get build-dep python-matplotlib**. I was prompted with a list of dozens of dependencies.  But I could see that they were all the dependencies needed by Python 2.x -- which is just what you would expect from the python-matplotlib repository.  It contains Matplotlib 1.1.1, which only supports Python 2.x.  I aborted before I actually installed any packages.

---

### Post by schragge on 2013-04-17
Check your default python version: ```
python -V
```
If it's 2.7, you probably need to build it with ```
python3 setup.py build
```

---

### Post by iMac71 on 2013-04-17
(not strictly connected to your issue, but anyway somewhat helpful for it) you might create an alias as follows:
[LIST=1]
[*]open a Terminal window and type (or copy & paste) into it```
alias python='/usr/bin/python3.2' >> .bash_aliases
``` 
[*]close the Terminal window and reopen it 
[/LIST]
now you should have python3 as default python, hence you should be able to install matplotlib without problems by typing```
python setup.py build
```in a Terminal window.

---

### Post by ladasky on 2013-04-17
Thank you schragge and iMac71, the problem was that Python 3.2 is not the default Python in Ubuntu (yet?), at least not as of version 12.04.1.

I changed my **.bash_aliases** file as suggested, and then proceeded beyond my error message.  I still had a few more packages to install, but I eventually finished the build without error messages.

For the record: the packages missing from the default installation of Ubuntu 12.04.1 which appear to be needed to install Matplotlib are not spelled out as explicitly in the Matplotlib docs as one would hope.  No mention is made of needing **g++**.  (Is **g++** packaged with **gcc** in other Linux installations?) The docs tell you that you need **Python** (of course), **numpy**, **libpng**, and **freetype**.  What the docs do not say is that the necessary header files for the build process are in the ***-dev** packages, not in the base packages.

Now, when I followed up with a **sudo python setup.py install**, I got an error message indicating a failure to find Python.h all over again!  But I could see from the log that Python 2.7 was being called.  So I tried **sudo python3 setup.py install**, and that worked.  

This may just be a one-time issue, but it has now got me wondering whether I should also make Python 3 the default for root as well.  I don't know whether that would cause problems.  If making Python 3 the default for root is a good idea, I'm not sure where I would find root's **.bash_aliases** file...

---

### Post by iMac71 on 2013-04-18
> **ladasky said:**
> I'm not sure where I would find root's **.bash_aliases** file...to use your ~/.bash_aliases as root, add the following lines to your /root/.bashrc```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
if [ -f $HOME/.bash_aliases ]; then
    . $HOME/.bash_aliases
fi
```tip found here: [http://7enn.com/2011/02/20/how-to-make-your-bash-aliases-available-as-a-root-in-ubuntu/](http://7enn.com/2011/02/20/how-to-make-your-bash-aliases-available-as-a-root-in-ubuntu/)
I only changed /home/[YOUR USER NAME] with $HOME in lines 4 & 5 of the original code.

---

### Post by schragge on 2013-04-18
> **iMac71 said:**
> I only changed /home/[YOUR USER NAME] with $HOME in lines 4 & 5 of the original code.You shouldn't have changed it. :) Original code sourced */home/regular_user_name/.bash_aliases* if it existed. You code just sources */root/.bash_aliases* twice. Also note that by default */root/.bashrc* only gets executed for interactive shell sessions, i.e. *sudo su* / *sudo -s*. On Ubuntu, *.bashrc* also gets sourced from *.profile*, but since you don't login as root, */root/.profile* usually don't get executed either. It gets executed when you *sudo su -* / *sudo -i* however, as these commands emulate logging in as root.

This means the OP will need either *sudo python3* or *sudo -i python* anyway, and rightly so. Permanently changing the default python interpreter (e.g. using *update-alternatives*) is a bad idea IMHO. There are many system python scripts and they obviously get tested only with python 2.7 which is still default on Ubuntu 12.04.

---

### Post by ladasky on 2013-04-28
> **schragge said:**
> Permanently changing the default python interpreter (e.g. using *update-alternatives*) is a bad idea IMHO. There are many system python scripts and they obviously get tested only with python 2.7 which is still default on Ubuntu 12.04.

Yes, I had this concern myself.  And I did not change the default Python for root for that reason.

---

### Post by MadCow108 on 2013-04-28
the problem is most likely just a missing python3-dev
you don't get that from apt-get build-dep because the 12.04 package has no python3 support (it has in 13.04)

> apt-get install python3-tk python3-dev python3-numpy libfreetype6-dev libpng12-dev tk8.5-dev
should be sufficient to build matplotlib 1.2.1 on 12.04, you may need more depending on which backends you want
add python3-pyqt4 for a qt backend

there is also a ppa that should work fine:
[https://launchpad.net/~takluyver/+archive/python3](https://launchpad.net/~takluyver/+archive/python3)

---

### Post by ladasky on 2013-04-28
MadCow108, thanks for your reply.  I actually got Matplotlib 1.2.1 to build on top of on Python 3.

Unfortunately, the only backend that I have succeeded to get working is the Agg backend.  I can write PNG files to disk, but I can't display live graphs from a Python application.  I've taken this issue to the Matplotlib mailing list, but I'll share a summary here.

Back when I was programming in Python 2.7, I was using the WxAgg backend, and I didn't even know that I was.  I had installed wxPython, and when I built Matplotlib, it automatically built the WxAgg backend for me.  Unfortunately, wxPython is NOT yet Python3 compatible. I thought I would try the GTKAgg backend, but I wasn't able to get wxGTK for Python 3 installed.  

I am contemplating upgrading to Ubuntu 13.04, in hope that some of these issues are resolved by newer repositories.

---

### Post by MadCow108 on 2013-04-29
I forgot you still need tk8.5-dev for the python3 tkagg
a python3 gtk backend is not available (py3 gtk exists but matplotlib 1.2.1 does not support it)
a wx backend is not possible yet as (stable) wx is not ported to python3 yet.

python3 qt backend should be possible in precise by installing python3-pyqt4

---

