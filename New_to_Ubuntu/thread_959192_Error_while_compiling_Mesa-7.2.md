---
title: "Error while compiling Mesa-7.2"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by sapan on 2008-10-26
I got the following error.(!!I am a begginer for Linux!!)
/usr/bin/ld: cannot find -lXmu
collect2: ld returned 1 exit status
mklib: Installing libglut.so.3.7.1 libglut.so.3 libglut.so in ../../../lib
mv: cannot stat `libglut.so.3.7.1': No such file or directory
make[3]: *** [../../../lib/libglut.so] Error 1
make[3]: Leaving directory `/home/balbir/Desktop/Mesa-7.2/src/glut/glx'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/balbir/Desktop/Mesa-7.2/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/balbir/Desktop/Mesa-7.2'
make: *** [linux-x86] Error 2

---

### Post by Dedoimedo on 2008-10-26
Hello,
Can you please explain the whole sequence of events?
Did you run configure before hand? Where did you get your package? What distro (version, architecture)? Do you have the build libraries installed?
Dedoimedo

---

### Post by sapan on 2008-10-26
Thanks for Paying attention.
I had downloded 3 packages(MesaLib-7.2,MesaGlut-7.2,MesaDemo..)From Source forge.net.I had followed instruction given in mesa3d.org.After unpacking these folders I used command >make linux-86.
Mine linux is ubuntu8.04 LTS Desktop edition.Processor Family is x86(2.93GHz).
While compiling ***: No such file or directory error came out some times, but I just search in internet and used sudo apt-get.. to update the Libraries.but this time I really stucked.

---

### Post by Dedoimedo on 2008-10-26
Hello,
Let me take a look at these packages, gimme a few days, I'll get back to you if I find anything useful.
Dedoimedo

---

