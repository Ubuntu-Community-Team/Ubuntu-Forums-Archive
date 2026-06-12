---
title: "Pyinstaller + PyQt + Matplotlib error"
date: 2010-06-10
forum: Programming Talk
---

### Post by malaui on 2010-06-10
I'm tryng to generate the executable of a python code using matplotlib and pyqt that I made.
I could sucessfuly generate the executable using pyinstaller, without erros. I'm also able to execute it in my own pc, where I create the executable. But when I try to run it in another pc I get this error:

```
[alunos@localhost Main]$ ./Main
/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib:574: UserWarning: Could not find matplotlibrc; using defaults
/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib:635: UserWarning: could not find rc file; returning defaults
Traceback (most recent call last):
  File "<string>", line 3, in <module>
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 436, in importHook
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 521, in doimport
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/Codigo", line 4, in <module>
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 436, in importHook
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 521, in doimport
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/Grafico", line 2, in <module>
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 436, in importHook
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 521, in doimport
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib.backends.backend_qt4agg", line 9, in <module>
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 436, in importHook
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 521, in doimport
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib.figure", line 19, in <module>
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 436, in importHook
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 521, in doimport
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib.axes", line 12, in <module>
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 436, in importHook
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 521, in doimport
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib.axis", line 10, in <module>
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 436, in importHook
  File "/home/patricia/Downloads/pyinstaller-1.4/iu.py", line 521, in doimport
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib.font_manager", line 1301, in <module>
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib.font_manager", line 1292, in _rebuild
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/matplotlib.font_manager", line 967, in __init__
  File "/home/patricia/Downloads/pyinstaller-1.4/Main/build/pyi.linux2/Main/outPYZ1.pyz/posixpath", line 67, in join
AttributeError: 'NoneType' object has no attribute 'endswith'
```

I dont know if I made it right, I just follow the instructons in READ ME file without any other configurations.
The instructions in READ ME file was:

>  Non-Windows users should first build the bootloader:
    cd source/linux
    python ./Make.py
    make

 Everyone should:
    python Configure.py
    python Makespec.py /path/to/yourscript.py
    python Build.py /path/to/yourscript.spec
    .done.



Do I have to specify where is matplotlib? If so, how can I do this? I read something about iu.py but I was not able to use it properly.


And why does it show my own pc directory here: File "/home/patricia/Downloads/pyinstaller-1.4/ in spite of the directory of the pc I'm using (alunos, not patricia)?

I'm using pyqt4, python 2.6, ubuntu 9.10 to generate and 10.04 to run, matplotlib 0.99 and pyinstaller 1.4


Thanks in advance,
I would appreciate any help =p

---

### Post by juancarlospaco on 2010-06-10
*python-packager.com*

why do you want do to these?, make a deb

---

### Post by malaui on 2010-06-10
Because I didnt want to have to install the software, I just want to run it in a computer without the necessary libraries.

---

### Post by malaui on 2010-06-10
I generated the deb through the site you gave me, and unfortunately I got a similar error:

> Traceback (most recent call last):
  File "<string>", line 3, in <module>
  File "/Python-Packager/Build-Server/pyinstaller-2.6/iu.py", line 436, in importHook
  File "/Python-Packager/Build-Server/pyinstaller-2.6/iu.py", line 521, in doimport
  File "/Python-Packager/Build-Server/application-builds/linux_deb/416/build/pyi.linux2/Pacote/outPYZ1.pyz/Codigo", line 1, in <module>
  File "/Python-Packager/Build-Server/pyinstaller-2.6/iu.py", line 436, in importHook
  File "/Python-Packager/Build-Server/pyinstaller-2.6/iu.py", line 495, in doimport
  File "/Python-Packager/Build-Server/pyinstaller-2.6/iu.py", line 297, in getmod
  File "/Python-Packager/Build-Server/pyinstaller-2.6/archive.py", line 468, in getmod
  File "/Python-Packager/Build-Server/pyinstaller-2.6/iu.py", line 109, in getmod
ImportError: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by ./libQtGui.so.4)

I dont know what to do...

---

### Post by xuampy on 2012-05-15
> **malaui said:**
> I generated the deb through the site you gave me, and unfortunately I got a similar error:



I dont know what to do...

I'm having the exact same problem here. I can't freeze and move around freely with this, since I keep having this problem. The workaround that I found was to install the python-matplotlib package on the target machine.

This obviously goes against the main idea of a "freezed" binary. 

I know that this is an old post, but did you came by a solution in all this time?

---

### Post by langloispy on 2012-06-01
Hi malaui and xuampy,

I experienced the same problem and the following work around worked for me. The binary version of the script looks for the file /etc/matplotlibrc. The only thing I needed to do was to copy that file from the compile machine to the destination machine. This allow the script to run but without font :( 

But this is a step forward..

I have installed the package ttf-dejavu-core ttf-freefont ttf-lyx to make the fonts working.

Pierre-Yves

---

