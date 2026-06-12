---
title: "Problem with scons: &quot; No SConstruct file found&quot;"
date: 2007-11-14
forum: Programming Talk
---

### Post by lenn-art on 2007-11-14
I tried to compile the unreleased version of lprof (GUI for argyllcms, to calibrate my display with a hardwaredevice). The last step a developer mailed me, is this one:

> 4) after that, you can try to build lprof. You will need to know where you have QT installed on your system (QTDIR)
scons PREFIX=/usr/local qt_directory=QTDIR
scons install

But there are some things i don't know:
- what is exactly my QTdir? There are several folders named /QT4
- do i have to run this command in the /src directory of lprof?
- every time i run the first command i get the error > scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 1128, in _main


---

### Post by rafafredd on 2008-03-31
Argh! I'm trying to compile ardour, and I get the exact same error you are having... Tried to reinstall scons three times, but the error perssits..

---

### Post by Xbehave on 2008-06-15
I fixed this problem by getting into the right directory scons is just like make, it will only work if your IN the directory with the sconstruct file

OLD:
different line
```
File /usr/lib/scons/SCons/Script/Main.py, line 825, in _main
```

for me but same problem

---

