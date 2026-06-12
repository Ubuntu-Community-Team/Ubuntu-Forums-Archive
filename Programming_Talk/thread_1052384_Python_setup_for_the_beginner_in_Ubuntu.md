---
title: "Python setup for the beginner in Ubuntu"
date: 2009-01-27
forum: Programming Talk
---

### Post by Cornbreadly on 2009-01-27
I am starting out in python and I am getting tripped up on little things.  

For example, right now I can't install a module through the 

```
python setup.py install
``` 

because I dont have read write access to the /usr/local/lib/python2.5/ directory.

I found an easy_install script that looks like it will help but it seems my ubuntu system isnt co-operating.  I tried sudo, sudo -i in order to install the modules, but I keep getting the same errors.  

Here is the error
```
root@eric-desktop:/home/eric/Desktop/cx_Freeze-4.0.1# python setup.py install
running install
running build
running build_py
running build_ext
building 'cx_Freeze.util' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -c source/util.c -o build/temp.linux-i686-2.5/source/util.o
source/util.c:6:20: error: Python.h: No such file or directory
source/util.c:370: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
source/util.c:384: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_ModuleMethods’
source/util.c: In function ‘initutil’:
source/util.c:404: error: ‘PyObject’ undeclared (first use in this function)
source/util.c:404: error: (Each undeclared identifier is reported only once
source/util.c:404: error: for each function it appears in.)
source/util.c:404: error: ‘module’ undeclared (first use in this function)
source/util.c:406: warning: implicit declaration of function ‘Py_InitModule’
source/util.c:406: error: ‘g_ModuleMethods’ undeclared (first use in this function)
error: command 'gcc' failed with exit status 1
root@eric-desktop:/home/eric/Desktop/cx_Freeze-4.0.1# 

```

---

### Post by cabalas on 2009-01-27
I don't know much about manually installing python modules, but I do have some experience using the gcc and to me it looks like you don't have the development libraries for python installed. Install python-dev from the repositories and try again, I think that should do the trick.

---

### Post by CptPicard on 2009-01-27
And of course you shouldn't try a manual installation as the first thing, most of the stuff is already in the repositories and should be installed through apt.

---

### Post by Cornbreadly on 2009-01-27
Thanks cabalas!  That did it.

---

### Post by Cornbreadly on 2009-01-27
Well actually no, now I am getting some news errors with the dev files installed for python 2.4-2.5.  It is a long one.
```
eric@eric-desktop:~$ cd /home/eric/Desktop/py2exe-0.6.9
eric@eric-desktop:~/Desktop/py2exe-0.6.9$ python setup.py install
running install
running build
running build_py
running build_ext
building '_memimporter' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DPYTHONDLL=\"PYTHON25.DLL\" -DPYTHONCOM=\"pythoncom25.dll\" -I/usr/include/python2.5 -c source/MemoryModule.c -o build/temp.linux-i686-2.5/source/MemoryModule.o
<command-line>: warning: missing terminating " character
<command-line>: warning: missing terminating " character
source/MemoryModule.c:30: warning: ignoring #pragma warning 
source/MemoryModule.c:32:21: error: Windows.h: No such file or directory
source/MemoryModule.c:33:19: error: winnt.h: No such file or directory
In file included from source/MemoryModule.c:42:
source/MemoryModule.h:38: warning: function declaration isn&#8217;t a prototype
source/MemoryModule.h:45: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;MemoryGetProcAddress&#8217;
source/MemoryModule.h:49: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;MyFreeLibrary&#8217;
source/MemoryModule.h:50: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;MyLoadLibrary&#8217;
source/MemoryModule.h:51: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;MyGetProcAddress&#8217;
source/MemoryModule.h:52: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; 
```

Then it does that for A WHILE...

```

source/MemoryModule.c:677: error: &#8216;struct tagMEMORYMODULE&#8217; has no member named &#8216;modules&#8217;
source/MemoryModule.c:680: error: &#8216;struct tagMEMORYMODULE&#8217; has no member named &#8216;codeBase&#8217;
source/MemoryModule.c:682: error: &#8216;struct tagMEMORYMODULE&#8217; has no member named &#8216;codeBase&#8217;
source/MemoryModule.c:682: error: &#8216;MEM_RELEASE&#8217; undeclared (first use in this function)
source/MemoryModule.c:684: error: &#8216;struct tagMEMORYMODULE&#8217; has no member named &#8216;name_table&#8217;
source/MemoryModule.c:685: error: &#8216;struct tagMEMORYMODULE&#8217; has no member named &#8216;name_table&#8217;
source/MemoryModule.c:687: warning: implicit declaration of function &#8216;HeapFree&#8217;
error: command 'gcc' failed with exit status 1
eric@eric-desktop:~/Desktop/py2exe-0.6.9$ 

```

---

### Post by cabalas on 2009-01-27
A couple of quick questions about the module you are trying to install:

[LIST=1]
[*] Is is available in the ubuntu repositories?
[*] Do the maintainers of that module offer a .deb package for it?
[*] Do you have all the dependencies installed for the module?
[*] Is this module designed to work on linux?
[/LIST]

If the answer to the 1st or 2nd question is yes then you should use them to install the module. I ask the last one because it would appear that the compiler is looking for windows specific headers.

---

### Post by snova on 2009-01-27
> **Cornbreadly said:**
> ```
source/MemoryModule.c:32:21: error: Windows.h: No such file or directory
source/MemoryModule.c:33:19: error: winnt.h: No such file or directory
```

I would guess this module is Windows-only. Says right on their home page:

> py2exe is a Python Distutils extension which converts Python scripts into executable **Windows** programs, able to run without requiring a Python installation.

---

### Post by Cornbreadly on 2009-01-27
I didn't know it would be OS specific. 

I wrote a script at home on my Ubuntu desktop that I want to turn into an executable for a use on work XP machines.

Red tape stops me from going around to everyone's pc who needs it and installing python and making the script executable from the desktop.  I just need something i can email around.

Google lead me to believe that py2exe would be the best choice.  I am open to anything that is simplier.  I would like to get it working tonight.

> py2exe is a Python Distutils extension which converts Python scripts **into** executable Windows programs, able to run without requiring a Python installation. 

---

