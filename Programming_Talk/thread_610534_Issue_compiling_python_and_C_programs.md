---
title: "Issue compiling python and C programs"
date: 2007-11-12
forum: Programming Talk
---

### Post by threethirty on 2007-11-12
I'm having trouble compiling python-twitter on my gutsy 32 bit box.  I'm trying to do [this]("http://philwilson.org/blog/2007/03/post-to-twitter-from-ubuntu-deskbar.html") but I am having issues.  I have no idea what I am doing (not really a programmer) , and I tried to post to their mailing list but I think that I was removed or not approved.  

here is what I posted to the mailing list, I think that I covered everything the first time so I am going to repost....

Ok here is what I did to get this far. I installed simplejson, I had
to do the ez_install because I was getting an error (which I have
totally forgotten at this point). Then I ran "setup.py build" and it
was fine, but when I go to run "setup.py install" I get the following
error:
```
**********************************************************************


WARNING: The C extension could not be compiled, speedups are not
enabled.

Above is the output showing how the compilation failed.

**********************************************************************

error: Setup script exited with error: can't copy 'simplejson.egg-info/
native_libs.txt': doesn't exist or not a regular file

```

Now I am very sure that simplejson.egg-info/native_libs.txt exists
because I can open it. So what have I done wrong? here is my terminal output:

```
three@Condor:~$ cd /home/three/python-twitter-0.5
three@Condor:~/python-twitter-0.5$ sudo python setup.py build
running build
running build_py
creating build
creating build/lib
copying twitter.py -> build/lib
running egg_info
writing requirements to python_twitter.egg-info/requires.txt
writing python_twitter.egg-info/PKG-INFO
writing top-level names to python_twitter.egg-info/top_level.txt
writing dependency_links to python_twitter.egg-info/
dependency_links.txt
reading manifest file 'python_twitter.egg-info/SOURCES.txt'
writing manifest file 'python_twitter.egg-info/SOURCES.txt'
three@Condor:~/python-twitter-0.5$ sudo python setup.py install
running install
running bdist_egg
running egg_info
writing requirements to python_twitter.egg-info/requires.txt
writing python_twitter.egg-info/PKG-INFO
writing top-level names to python_twitter.egg-info/top_level.txt
writing dependency_links to python_twitter.egg-info/
dependency_links.txt
reading manifest file 'python_twitter.egg-info/SOURCES.txt'
writing manifest file 'python_twitter.egg-info/SOURCES.txt'
installing library code to build/bdist.linux-i686/egg
running install_lib
running build_py
creating build/bdist.linux-i686
creating build/bdist.linux-i686/egg
copying build/lib/twitter.py -> build/bdist.linux-i686/egg
byte-compiling build/bdist.linux-i686/egg/twitter.py to twitter.pyc
creating build/bdist.linux-i686/egg/EGG-INFO
copying python_twitter.egg-info/PKG-INFO -> build/bdist.linux-i686/egg/
EGG-INFO
copying python_twitter.egg-info/SOURCES.txt -> build/bdist.linux-i686/
egg/EGG-INFO
copying python_twitter.egg-info/dependency_links.txt -> build/
bdist.linux-i686/egg/EGG-INFO
copying python_twitter.egg-info/requires.txt -> build/bdist.linux-i686/
egg/EGG-INFO
copying python_twitter.egg-info/top_level.txt -> build/bdist.linux-
i686/egg/EGG-INFO
zip_safe flag not set; analyzing archive contents...
creating dist
creating 'dist/python_twitter-0.5-py2.5.egg' and adding 'build/
bdist.linux-i686/egg' to it
removing 'build/bdist.linux-i686/egg' (and everything under it)
Processing python_twitter-0.5-py2.5.egg
Removing /usr/lib/python2.5/site-packages/python_twitter-0.5-py2.5.egg
Copying python_twitter-0.5-py2.5.egg to /usr/lib/python2.5/site-
packages
python-twitter 0.5 is already the active version in easy-install.pth

Installed /usr/lib/python2.5/site-packages/python_twitter-0.5-
py2.5.egg
Processing dependencies for python-twitter==0.5
Searching for simplejson
Reading http://pypi.python.org/simple/simplejson/
Reading http://undefined.org/python/#simplejson
Best match: simplejson 1.7.3
Downloading http://pypi.python.org/packages/source/s/simplejson/simplejson-1.7.3.tar.gz#md5=03935eda1211f29d6856481baf6cba59
Processing simplejson-1.7.3.tar.gz
Running simplejson-1.7.3/setup.py -q bdist_egg --dist-dir /tmp/
easy_install-JeIvTE/simplejson-1.7.3/egg-dist-tmp-D6v4Lj
simplejson/_speedups.c:1:20: error: Python.h: No such file or
directory
simplejson/_speedups.c:9: error: expected ')' before 'c'
simplejson/_speedups.c:10: error: expected '=', ',', ';', 'asm' or
'__attribute__' before '*' token
simplejson/_speedups.c:12: error: expected '=', ',', ';', 'asm' or
'__attribute__' before '*' token
simplejson/_speedups.c:14: error: expected '=', ',', ';', 'asm' or
'__attribute__' before '*' token
simplejson/_speedups.c:28: error: expected ')' before 'c'
simplejson/_speedups.c:72: error: expected '=', ',', ';', 'asm' or
'__attribute__' before '*' token
simplejson/_speedups.c:120: error: expected '=', ',', ';', 'asm' or
'__attribute__' before '*' token
simplejson/_speedups.c:180: error: expected ')' before string constant
simplejson/_speedups.c:185: error: expected '=', ',', ';', 'asm' or
'__attribute__' before '*' token
simplejson/_speedups.c:204: error: expected '=', ',', ';', 'asm' or
'__attribute__' before 'speedups_methods'
simplejson/_speedups.c: In function 'init_speedups':
simplejson/_speedups.c:213: error: 'PyObject' undeclared (first use in
this function)
simplejson/_speedups.c:213: error: (Each undeclared identifier is
reported only once
simplejson/_speedups.c:213: error: for each function it appears in.)
simplejson/_speedups.c:213: error: 'm' undeclared (first use in this
function)
simplejson/_speedups.c:214: warning: implicit declaration of function
'Py_InitModule4'
simplejson/_speedups.c:214: error: 'speedups_methods' undeclared
(first use in this function)
simplejson/_speedups.c:214: error: 'NULL' undeclared (first use in
this function)
simplejson/_speedups.c:214: error: 'PYTHON_API_VERSION' undeclared
(first use in this function)
**********************************************************************


WARNING: The C extension could not be compiled, speedups are not
enabled.

Above is the output showing how the compilation failed.

**********************************************************************

error: Setup script exited with error: can't copy 'simplejson.egg-info/
native_libs.txt': doesn't exist or not a regular file
three@Condor:~/python-twitter-0.5$
```

Thanks in advance!
three

---

### Post by Compyx on 2007-11-12
Looks like the installer needs some headers to link against Python. You should look in Synaptic for packages with 'python' and 'dev' in their name.

Sorry I can't be more helpful, I'm at work behind some horrid Windows box. When I get home I'll try to look into this some more.

---

### Post by zanglang on 2007-11-12
Yeah, Python.h is in the "python2.5-dev" package (or python2.4-dev if you're using the older version). You should be able to install that via apt-get to solve the errors.

---

### Post by pmasiar on 2007-11-12
> **threethirty said:**
>  I tried to post to their mailing list but I think that I was removed or not approved.  

Most mailing list let only list members to post, to cut down spammers a little. So subscribe to list first.

---

### Post by threethirty on 2007-11-12
Ok I tried to install python-all (it has 2.4 and 2.5) and it all went well except this error:
```
E: python-setuptools: subprocess post-installation script returned error exit status 1
```

---

### Post by leonardovarela on 2008-02-29
I have a similar problem:
I installed ubuntu 7.04 from the scratch, I upgraded to 7.10. I downloaded (TURBOGEARS)tgsetup.py. Then I ran it.
This is what I've got:
```

Running simplejson-1.7.4/setup.py -q bdist_egg --dist-dir /tmp/easy_install-ypfbsB/simplejson-1.7.4/egg-dist-tmp-8LLY1w
simplejson/_speedups.c:1:20: error: Python.h: No such file or directory
simplejson/_speedups.c:15: error: expected ')' before 'c'
simplejson/_speedups.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
simplejson/_speedups.c:18: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
simplejson/_speedups.c:20: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
simplejson/_speedups.c:34: error: expected ')' before 'c'
simplejson/_speedups.c:78: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
simplejson/_speedups.c:126: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
simplejson/_speedups.c:186: error: expected ')' before string constant
simplejson/_speedups.c:191: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
simplejson/_speedups.c:210: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'speedups_methods'
simplejson/_speedups.c: In function 'init_speedups':
simplejson/_speedups.c:219: error: 'PyObject' undeclared (first use in this function)
simplejson/_speedups.c:219: error: (Each undeclared identifier is reported only once
simplejson/_speedups.c:219: error: for each function it appears in.)
simplejson/_speedups.c:219: error: 'm' undeclared (first use in this function)
simplejson/_speedups.c:220: warning: implicit declaration of function 'Py_InitModule4'
simplejson/_speedups.c:220: error: 'speedups_methods' undeclared (first use in this function)
simplejson/_speedups.c:220: error: 'NULL' undeclared (first use in this function)
simplejson/_speedups.c:220: error: 'PYTHON_API_VERSION' undeclared (first use in this function)
**********************************************************************
WARNING: The C extension could not be compiled, speedups are not enabled.

Below is the output showing how the compilation failed:

command 'gcc' failed with exit status 1
**********************************************************************
error: Setup script exited with error: can't copy 'simplejson.egg-info/native_libs.txt': doesn't exist or not a regular file

```

I thought speedups may not be 'necessary' so I just gave it a try, but the very basics of turbogears (tg-admin) is not working.

Any help would be greatly appreciated.

---

### Post by andersb on 2008-03-23
I had the same problem but after running apt-get install python-simplejson it all worked just fine.

---

### Post by carbonsink on 2009-02-24
I had the same problem. I was able to install simplejson (as part of a pylons install) and have the simplejson 'speedups' compiled by doing these first:

apt-get install gcc [I didn't have GCC yet]
apt-get install python2.5-dev [from this thread, my python version is 2.5]
apt-get install libc6-dev [from the Pylons Book p.23]
apt-get install linux-headers-$(uname -r) [from some other random 'net page]

Ubuntu Server 8.04.2
VMware Server 2

BTW, running Ubuntu within VMware allows one to easily go back to an earlier version of the environment and redo the installation steps.

---

### Post by harky on 2009-10-02
I am having similar problems trying to install some software from source (msgbus-0.1). The problem is that the python2.5-dev IS installed. See error output below:
 
>  
$ make
make all-recursive
make[1]: Entering directory `/home/dharkness/msgbus-0.1'
Making all in chatdemo
make[2]: Entering directory `/home/dharkness/msgbus-0.1/chatdemo'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dharkness/msgbus-0.1/chatdemo'
Making all in src
make[2]: Entering directory `/home/dharkness/msgbus-0.1/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dharkness/msgbus-0.1/src'
Making all in python
make[2]: Entering directory `/home/dharkness/msgbus-0.1/python'
/usr/bin/python setup.py build
running build
running build_ext
building 'evmsg' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I.. -I../src -I -I/usr/include/python2.5 -c evmsg.c -o build/temp.linux-x86_64-2.5/evmsg.o
evmsg.c:4:20: error: Python.h: No such file or directory
evmsg.c:5:26: error: structmember.h: No such file or directory

 
And to verify that the python2.5 and the dev package are installed see the output from aptitude:
> $ aptitude search python2.5
p idle-python2.5 - An IDE for Python (v2.5) using Tkinter
v libapache2-mod-python2.5 -
i python2.5 - An interactive high-level object-oriented
 
$ aptitude search python2.5-dev
i A python2.5-dev - Header files and a static library for Pyth
 
Finally, to verify that the files are actually in /usr/include/python2.5 (which is one of the include parameters on the gcc command called by make):
> $ ls -l /usr/include/python2.5/
total 584
.
.
.
-rw-r--r-- 1 root root 4204 2009-07-22 11:53 Python.h
.
.
.
-rw-r--r-- 1 root root 2532 2009-07-22 11:53 structmember.h
.
.
.

 
Any help would be greatly appreciated as I cannot find anything other than "you need to install the python dev package" as a solution. And that has already been done here.
 
Thank You in advance for your help.

---

### Post by harky on 2009-10-02
For reference, my problem has been solved in this thread: [http://ubuntuforums.org/showthread.php?p=8041025](http://ubuntuforums.org/showthread.php?p=8041025)

---

### Post by medirock on 2010-03-30
> **zanglang said:**
> Yeah, Python.h is in the "python2.5-dev" package (or python2.4-dev if you're using the older version). You should be able to install that via apt-get to solve the errors.

i have a similar problem ....well actually i'm trying to install a simulator named netpylab  developed in python and each time i run the setup program via a cmd i got an error like :


warning: install_data: setup script did not provide a directory for 'netpylab\img'
 -- installing right in 'build\bdist.win32\egg'
error: can't copy 'netpylab\img': doesn't exist or not a regular file

well the img contains png images and i don't have a clue on why it couldn't not copy them...
if you know anything about this problem please try and explain it to me so i could resolve this because it has been at least a week that i was tryning in vain to figure that out....by the way, my OS is windows vista . thanks !

---

### Post by darrenleeweber on 2010-05-10
Put up a solution that works for me at

[http://psdlw.users.sourceforge.net/wordpress/?p=231](http://psdlw.users.sourceforge.net/wordpress/?p=231)

I hope that's helpful.

---

