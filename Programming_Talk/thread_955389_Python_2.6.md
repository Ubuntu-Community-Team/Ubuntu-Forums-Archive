---
title: "Python 2.6"
date: 2008-10-22
forum: Programming Talk
---

### Post by sheto on 2008-10-22
May I please know how to upgrade to Python version 2.6?
I googled "upgrading python 2.6 Ubuntu" but could not find any results.
I downloaded the source code from the Python website and executed the steps given in the Readme but I could it gave me an error in the second step, executing the "make" command. My output was something like this:


gcc -pthread -c -fno-strict-aliasing -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes  -I. -IInclude -I./Include   -DPy_BUILD_CORE -o Modules/config.o Modules/config.c
gcc -pthread -c -fno-strict-aliasing -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes  -I. -IInclude -I./Include   -DPy_BUILD_CORE -DPYTHONPATH='":plat-linux2:lib-tk:lib-old"' \
		-DPREFIX='"/usr/local"' \
		-DEXEC_PREFIX='"/usr/local"' \
		-DVERSION='"2.6"' \
		-DVPATH='""' \
		-o Modules/getpath.o ./Modules/getpath.c
gcc -pthread -c -fno-strict-aliasing -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes  -I. -IInclude -I./Include   -DPy_BUILD_CORE -DSVNVERSION=\"`LC_ALL=C svnversion .`\" -o Modules/getbuildinfo.o ./Modules/getbuildinfo.c
rm -f libpython2.6.a
ar cr libpython2.6.a Modules/getbuildinfo.o
ar cr libpython2.6.a Parser/acceler.o Parser/grammar1.o Parser/listnode.o Parser/node.o Parser/parser.o Parser/parsetok.o Parser/bitset.o Parser/metagrammar.o Parser/firstsets.o Parser/grammar.o Parser/pgen.o Parser/myreadline.o Parser/tokenizer.o
ar cr libpython2.6.a Objects/abstract.o Objects/boolobject.o Objects/bufferobject.o Objects/bytes_methods.o Objects/bytearrayobject.o Objects/cellobject.o Objects/classobject.o Objects/cobject.o Objects/codeobject.o Objects/complexobject.o Objects/descrobject.o Objects/enumobject.o Objects/exceptions.o Objects/genobject.o Objects/fileobject.o Objects/floatobject.o Objects/frameobject.o Objects/funcobject.o Objects/intobject.o Objects/iterobject.o Objects/listobject.o Objects/longobject.o Objects/dictobject.o Objects/methodobject.o Objects/moduleobject.o Objects/object.o Objects/obmalloc.o Objects/rangeobject.o Objects/setobject.o Objects/sliceobject.o Objects/stringobject.o Objects/structseq.o Objects/tupleobject.o Objects/typeobject.o Objects/weakrefobject.o Objects/unicodeobject.o Objects/unicodectype.o
ar cr libpython2.6.a Python/_warnings.o Python/Python-ast.o Python/asdl.o Python/ast.o Python/bltinmodule.o Python/ceval.o Python/compile.o Python/codecs.o Python/errors.o Python/frozen.o Python/frozenmain.o Python/future.o Python/getargs.o Python/getcompiler.o Python/getcopyright.o Python/getmtime.o Python/getplatform.o Python/getversion.o Python/graminit.o Python/import.o Python/importdl.o Python/marshal.o Python/modsupport.o Python/mystrtoul.o Python/mysnprintf.o Python/peephole.o Python/pyarena.o Python/pyfpe.o Python/pymath.o Python/pystate.o Python/pythonrun.o Python/structmember.o Python/symtable.o Python/sysmodule.o Python/traceback.o Python/getopt.o Python/pystrcmp.o Python/pystrtod.o Python/formatter_unicode.o Python/formatter_string.o Python/dynload_shlib.o   Python/thread.o
ar cr libpython2.6.a Modules/config.o Modules/getpath.o Modules/main.o Modules/gcmodule.o 
ar cr libpython2.6.a Modules/threadmodule.o  Modules/signalmodule.o  Modules/posixmodule.o  Modules/errnomodule.o  Modules/pwdmodule.o  Modules/_sre.o  Modules/_codecsmodule.o  Modules/zipimport.o  Modules/symtablemodule.o  Modules/xxsubtype.o
ranlib libpython2.6.a
gcc -pthread  -Xlinker -export-dynamic -o python \
			Modules/python.o \
			libpython2.6.a -lpthread -ldl  -lutil   -lm  
libpython2.6.a(posixmodule.o): In function `posix_tmpnam':
/home/kshitij/Python-2.6/./Modules/posixmodule.c:7074: warning: the use of `tmpnam_r' is dangerous, better use `mkstemp'
libpython2.6.a(posixmodule.o): In function `posix_tempnam':
/home/kshitij/Python-2.6/./Modules/posixmodule.c:7029: warning: the use of `tempnam' is dangerous, better use `mkstemp'
running build
running build_ext

Failed to find the necessary bits to build these modules:
_bsddb             _curses            _curses_panel   
_hashlib           _sqlite3           _ssl            
bsddb185           bz2                dbm             
readline           sunaudiodev                        
To find the necessary bits, look in setup.py in detect_modules() for the module's name.

running build_scripts


I could not find what to install in the setup.py file.
Could somebody please help?
Thanking you in advance.

---

### Post by jimi_hendrix on 2008-10-22
looks like you need to install

_bsddb             _curses            _curses_panel   
_hashlib           _sqlite3           _ssl            
bsddb185           bz2                dbm             
readline           sunaudiodev

---

### Post by sheto on 2008-10-22
Could you please tell me how to do this? I could not find these packages in Synaptic.

---

### Post by Paul Miller on 2008-10-22
If you do apt-get install python-dev, it will install all the build dependencies for Python 2.5, which are the same as the ones for 2.6.

---

### Post by sheto on 2008-10-23
I posted this thread when I had the latest version of python-dev installed. That does not seem to be working :(

---

### Post by unoodles on 2008-10-23
I think your best shot is:
sudo apt-get build-dep python

---

### Post by pmasiar on 2008-10-23
My advise would be: don't upgrade Python if you are not ready to solve any problems with dependencies. many of your programs depend on Python and if you change it, something might go wrong.

Much safer choice is to wait until stock Python in ubuntu will be 2.6. 

Do you need some particular libraries? install them. Do you need some features? Many can be installed via "from __future__ install ...."

Don't mess with your system if you don't know what are you doing.

---

### Post by Majorix on 2008-10-23
There are a few changes from Py25 to Py26 which might leave a Py26 interpreter clueless on how to act on a Py25 code, and there are usually at least a few dozen Py25 scripts on your Linux system. I would leave Py26 alone for now unless you want trouble.

---

### Post by Vox754 on 2008-10-23
> **pmasiar said:**
> 
Don't mess with your system if you don't know what are you doing.

Don't mess with your system if you don't know what are you doing!!!

---

### Post by bobbocanfly on 2008-10-23
> **Vox754 said:**
> Don't mess with your system if you don't know what are you doing!!!

Or if you are drunk and think you know what you are doing. I learned this the hard way upgrading to Intrepid 2 days after the repositories were open. Epic, epic failure ensued. I can see the same thing happening here...

---

### Post by sheto on 2008-10-25
Thanks, guys. I'll wait.

---

### Post by yanom on 2008-12-06
if you are installing system-wide (doing it as root or with sudo) then after you install, make sure that /usr/bin/python is a symbolic link to /usr/bin/python2.5, and that ```
 $ python 
``` starts python 2.5


i tried what you are doing as root, it was a long headache involving apt-get, symbolic links, and swearing.

---

### Post by nvteighen on 2008-12-07
And why not installing it into your home folder? That won't disrupt your system.

---

### Post by bobbocanfly on 2008-12-07
> **nvteighen said:**
> And why not installing it into your home folder? That won't disrupt your system.

I installed Python 3.0 the day it came out and installing it alongside another Python version is very safe (I'm guessing its the same for 2.6). By default (running ./configure, make, make install) with *not* overwrite any other version of python. You can call it by running pythonX.X. "python" will just run the default 2.5 install.

---

### Post by Claus7 on 2008-12-07
Hello,

I'm not so sure. I installed python 2.5.2, while dapper had 2.4 as the latest version supported. Every time I open synaptic I get that I have destroyed packages. 

I'm not so sure if python was the problem, because I installed other packages from source as well.

Regards!

---

### Post by gilgy on 2009-01-08
> **Claus7 said:**
> Hello,

I'm not so sure. I installed python 2.5.2, while dapper had 2.4 as the latest version supported. Every time I open synaptic I get that I have destroyed packages. 

I'm not so sure if python was the problem, because I installed other packages from source as well.

Regards!

I got the same issue as well. I was tinkering on Python 2.6, and it actually blew the dependencies to bits! I have a LOT of broken dependencies, so I had no choice (I think) but to do a clean-install (which I didn't mind, really, since I was planning on making drastic changes on my computer as well):D.

One thing though, was there a way to even uninstall Python 2.6 without having to do a clean-install, like I did? I installed it using the .tgz file, so there's no way for me to uninstall it through apt-get or synaptic. (I didn't use checkinstall. Too bad....)

---

### Post by pmasiar on 2009-01-08
IIRC Python 3000 will have support for multiple versions. Until then, use the version installed by default :-)

---

### Post by Kilon on 2009-01-08
I had the same problem with MACOS , I installed python 2.6 and then BOING!!! , nothing worked. Could not start IDLE or the interpreter and of course I could not execute my python programs. Googled a bit and found out that someone messed up the build for MACOS, and have not corrected the minor problem after 15 days!!! They expected that everyone will compile from source. I tried to compile from source but my bash Terminal , has no "make" or "install" command so that proven to be more of a hassle that it deserved. 

So I will have to agree with pmasiar here, if something works to you DO NOT UPGRADE. specially when the upgrade is very new and not tested. 
[B][U]
Let others be "Ginny pigs".    [/U][/B]

> **pmasiar said:**
> IIRC Python 3000 will have support for multiple versions. Until then, use the version installed by default :-)

Wait a Sec , is it not python 3000 already released ? 

[http://www.python.org/download/releases/3.0/](http://www.python.org/download/releases/3.0/)

---

### Post by ssam on 2009-01-08
openSUSE 11.1 has python 2.6 (i have not spotted any other big distros with it yet). you could run it in a virtual machine.

---

### Post by .Maleficus. on 2009-01-08
> **ssam said:**
> openSUSE 11.1 has python 2.6 (i have not spotted any other big distros with it yet). you could run it in a virtual machine.
Arch Linux has Python 2.6 (after you pacman -S python anyways).  The changes from 2.5 to 2.6 weren't all that big (mostly to make the transition to 3.0 easier) so all of the things that I wrote worked fine, however after changing the symlink to 2.6 it really screwed up something with Synaptic, to the point were I couldn't uninstall or install *anything*.  Not a big deal on Arch, but on Ubuntu keep 2.5 for now.

---

### Post by yanom on 2009-01-08
what if i download the python 2.5.4 source, run the install instructions as root, thus making the default python 2.5.4, will this cause any problems?

---

### Post by Claus7 on 2009-01-09
Hello,

> **gilgy said:**
> I got the same issue as well. I was tinkering on Python 2.6, and it actually blew the dependencies to bits! I have a LOT of broken dependencies, so I had no choice (I think) but to do a clean-install (which I didn't mind, really, since I was planning on making drastic changes on my computer as well):D.

One thing though, was there a way to even uninstall Python 2.6 without having to do a clean-install, like I did? I installed it using the .tgz file, so there's no way for me to uninstall it through apt-get or synaptic. (I didn't use checkinstall. Too bad....)

So it was python after all that made all the mess. Lucky me I installed it with checkinstall, so it is easy for me to uninstall it (at least this is what I think!).

> **yanom said:**
> what if i download the python 2.5.4 source, run the install instructions as root, thus making the default python 2.5.4, will this cause any problems?

I think that you will find your answer in this thread, where it sais that you can install it, yet NOT to the default folders, but to your home for example. If you do so, the old python with the new one will cause conflicts, at least this is what I get having in synaptic the broken packages. What I would advice you is to type make checkinstall, instead of make install. That way a nice and beautiful string of the version you installed will be displayed in synaptic. As a result you will have the ability to remove it from your system with one click away. I haven't done it myself though, because up to now my system is working nicely, so I do not want to mess anything (even though I have broken packages in synaptic!).

Also I see that you have made a link with the version you want to install, and if I understand correctly it is working. Also from here :
[http://ubuntuforums.org/showthread.php?p=6451074#post6451074](http://ubuntuforums.org/showthread.php?p=6451074#post6451074)
you post about your problem. Pardon me, yet I do not understand what exactly you want to do. You are referring to three different versions of python:
2.5.2, 2.5.4, 2.6. Why do you need three? Could you be a little more precise? I think that we have similar questions as far as a new version installment of python is concerned.

And now a more general discussion (concering the topic of the thread):
I do know that there are three kinds of libraries in general. These are the static ones, the shared ones and dynamically loaded.
I kindly provide you with this link in which they are explained very comprehensively:
[http://www.dwheeler.com/program-library/](http://www.dwheeler.com/program-library/)

I'm still not sure though, about how exactly libraries work and in specific what it will happen, if for example I install python 2.5 on top of python 2.4.
I do not care so much about programming in this library. I do care about the dependencies. How I will inform my system that the old programs should use the old python and a new program the new version of python? One solution is installing it in another folder. Yet, what exactly happens if I install the one on top of the other? Is it easy enough to inform even the old programs to use this new version and get rid safely with the old one?
In my case the command:
sudo apt-get install -f
which is proposed as one that *resolves* broken pagkages in my case the only thing that it does is to propose me to *remove* the broken packages. I think that the same command is proposed in order to solve the dependencies (correct me if I'm wrong).

Regards!

---

### Post by AnRa on 2009-01-09
You may try using [this PPA](https://launchpad.net/~doko/+archive).

---

### Post by Claus7 on 2009-01-09
Hello,

> **AnRa said:**
> You may try using [this PPA](https://launchpad.net/~doko/+archive).

This seems to me to be the easy way. Install deb packages with just one click away. What happens if the packages are not availabe in deb and/or if the version of ubuntu is a little bit old and is not supported by one?

Regards!

---

### Post by yanom on 2009-01-09
i wanted to install 2.5.4 on top of 2.5.2, because they are both part of Python 2.5, and 2.5.4 has some bug-fixes.

---

### Post by casevh on 2009-01-09
Python 2.6 can be installed without overwriting the default Python installation. Just do:

./configure --prefix=/usr/local
make
sudo make altinstall

The key command is "altinstall". It won't overwrite the default installation. I typically create a symbolic link in /usr/local/bin called py26 that is linked to python2.6. Then "python" still refers to the default version and "py26" refers to your version. I frequently have py24, py25, py26, and py30 in additon to python.

To fix the missing libraries, you need to install the development libraries. For example, to fix the readline error,  you should install "libreadline5-dev". IMO, the readline module is the most important one. Python 2.6 has been built; just a few of the modules are missing (BSD - old database, curses - character-based user interface, SQlite - new database, and SSL/hashing support). If you don't use those libraries, don't worry about the error message.

casevh

---

### Post by pmasiar on 2009-01-10
> **Claus7 said:**
> So it was python after all that made all the mess.

Not exactly: it was clueless user who installed wrong package in a wrong way, and computer did exactly what is was told to do. :-)

If you **can** do something it does not mean it is right thing to do, and you should do it. Think before jumping!

---

### Post by Claus7 on 2009-01-10
Hello,

> **pmasiar said:**
> Not exactly: it was clueless user who installed wrong package in a wrong way, and computer did exactly what is was told to do. :-)

If you **can** do something it does not mean it is right thing to do, and you should do it. Think before jumping!

no objection at all! You are absolutely right! And you put it kindly "clueless user". Yup, I was. Yet, how someone can learn if someone do not experiment a little? I'm using Dapper Drake for at least 2 years now, and I'm very content, even if for the past 4 months or so I have these broken packages, and I cannot install practicaly anything from synaptic. I have tried and built a lot of things, and this helped me so as to have a system configured in such a way that suits my needs. Now, if in the process something goes wrong, I'll try to fix it!

Really, I experimented because I was thinking to upgrade, so if something went wrong it was ok with me. Yet, I'm still using something that I have almost nothing to complain about (at least up to now). I think that Dapper is concidered one of the best distos not only for ubuntu "borders", yet for the entire linux flavors in general. What I wanted to do, was to install the new version of python because farsight for amsn depended on it. I messed it a little. Yet, things are working nicely up to now. And I want to avoid formatting every now and then my disk. I think that this is something possibly a windows user does often, because of viruses which cannot be removed. At least this is what I think.

Any information on how I will solve this issue will be welcome.
Regards!

---

### Post by pmasiar on 2009-01-10
You are 100% correct that you need to tinker with the system to learn and understand how it works, and you inevitably break something during the learning process.

My objection was againt your formulation "it was python after all that made all the mess" - because it might give some random reader a wrong impression that Python is safer to be avoided.

If you said "it was me, wrongly upgrading python after all that made all the mess" (which is what you ment, as I see from your response), all would be fine.

OK, no offense taken, no damage done, everything is just peachy. :-)

---

### Post by dmub82 on 2009-01-12
Teaching myself Python from the tutorial on docs.python.org, which uses 2.6, so I followed the advice in this thread and [here]("http://www.lysium.de/blog/index.php?/archives/229-Installing-Python-2.6-on-Ubuntu-8.04.html") to install it without breaking 2.5. That seems to have gone fine but I'm still getting one "failed to build this module" when I run "make". The module named is "_tkinter". I can run the 2.6 interpreter fine and the (very simple) stuff I try works as it should, is that going to be a problem later on?

Edit: I'm on Intrepid, btw. 

Nevermind, solved. sudo apt-get install tk8.5 tk.85-dev, if anyone else needs it.

---

### Post by bgs100 on 2009-01-13
I compiled 2.6 from source.  I killed my computer.  I BARELY managed to fix it.  It took like 5 days!!!  Half my apps were broken.  
I fixed it with this: [http://ubuntuforums.org/showpost.php?p=6268923&postcount=5](http://ubuntuforums.org/showpost.php?p=6268923&postcount=5)

---

### Post by Claus7 on 2009-01-15
Hello,

> **bgs100 said:**
> I compiled 2.6 from source.  I killed my computer.  I BARELY managed to fix it.  It took like 5 days!!!  Half my apps were broken.  
I fixed it with this: [http://ubuntuforums.org/showpost.php?p=6268923&postcount=5](http://ubuntuforums.org/showpost.php?p=6268923&postcount=5)

I followed your steps having in mind that I had installed manualy version 2.5.2 and wanted to go back to 2.4:
1. So, do "sudo nautilus" in terminal and go to /usr/local/bin.
2. Delete "python", "python2.*5*", "python2.*5*-config", and "python-config". 
3. Then, go to /usr/bin. 
4. copy "python2.*4*" and paste it into /usr/local/bin.
5. also copy "python2.*4*-config" and paste it into /usr/local/bin. [I have no such config file]
6. Make sure your in /usr/local/bin.
7. Copy "python2.5" and paste it in the same folder
8. Rename the copy "python"
9. Right click "python2.5-config" and hit "Make Link"
10.Rename the link "python-config"
[I cannot do steps 9 and 10 because I do not have such files]

The result of all the things that I made was that when I type python in therminal to have the 2.4 version and not the 2.5. I think that something is missing about the dependencies...I mean how you solved the broken packages in synaptic. Any ideas? Nice up to now.

EDIT: I saw desklets in my desktop after I restarted my system, after a long long time! Not bad!

Regards!

---

### Post by Claus7 on 2009-03-17
Hello,

problem solved:
[http://ubuntuforums.org/showthread.php?p=6913312#post6913312](http://ubuntuforums.org/showthread.php?p=6913312#post6913312)

Regards!

---

