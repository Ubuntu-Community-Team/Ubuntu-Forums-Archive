---
title: "HOWTO: Install OpenModelica environment?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by amelie on 2008-07-03
Hello everybody!
[This]("http://www.ida.liu.se/labs/pelab/modelica/OpenModelica/releases/1.4.4/src/") 
is the directory where I downloaded the files from, but I've got no idea how to install it on Ubuntu. I don't have internet on the Ubuntu machine as well... 
Thanks in advance if somebody can help me deal with it

---

### Post by phidia on 2008-07-03
Right click on the archieve you downloaded and select/click the "extract here" option. A new directory should have been created when the extraction finishes. Read the README file and perhaps the INSTALL file to see what you need to do to install.

---

### Post by fkafka on 2008-09-27
Hi, 

If you have no experience compiling and fixing
makefile in Linux then it will be a bit hard to
compile OpenModelica for yourself.

However, there are alternatives:
1. There is a (a bit older) static builded OpenModelica [here]("http://www.ida.liu.se/~pelab/modelica/OpenModelica/OMC/nightly-builds/i386-Linux/").
   Just follow the instructions to install.
2. There is a virtual machine image based on Ubuntu [here]("http://www.ida.liu.se/~pelab/modelica/OpenModelica/OMC/nightly-builds/VMware/").
   I guess this is the easiest to use. Just install vmplayer
   get the image and run it.
3. There is an older .deb package that might install on
   Ubuntu [here]("http://www.ida.liu.se/~pelab/modelica/OpenModelica/OMC/nightly-builds/i386-Linux/Ubuntu_6.10/").

Cheers,
za-k/

---

