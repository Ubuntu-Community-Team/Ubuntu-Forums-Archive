---
title: "FLTK compiled program uninstalation"
date: 2013-01-12
forum: Programming Talk
---

### Post by pepi55 on 2013-01-12
Hello guys,

Im new to these forums so excuse me for if im in the wrong section here.

now i havent ever used FLTK or compiled a program before but i somehow managed to install a program which i later found out, that i dont need at all. 

i used this command line:
```

g++ DoConfig.cpp -o DoConfigure -s $(fltk-config --cxxflags --ldflags)

```

now i want to uninstall the program and purge all fltk libs and stuff that goes with it accordingly.

also, i have no need for g++ anymore. I think
```

sudo apt-get remove g++ --purge

```
would do the job?

thanks in advance.

---

### Post by MadCow108 on 2013-01-13
this might do it:
> rm ./DoConfigure # in the folder you ran g++ from
apt-get autoremove --purge libfltk1.1-dev # or libfltk1.3-dev
autoremove will only work if you installed all fltk stuff via this one meta package
if you installed them manually you have to remove them manually (= list them all in apt-get remove)

---

### Post by pepi55 on 2013-01-13
thanks for the reply! 

i remember adding one package manually which asked for all the libs. Ill just try and see which package that exactly was.

However, I already manually removed the folder i did the compiling in through my window manager. is it removed or did i just #!@$ things up?

---

