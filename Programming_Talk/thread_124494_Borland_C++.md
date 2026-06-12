---
title: "Borland C++"
date: 2006-02-01
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-01
Hi,

I recently joined a new job and work over there demands coding in Borland C++.

Can it be done in Ubuntu or is there anything similar in Ubuntu ?

Another quick question, how different is it from normall C++ like g++ or MS Visual C++. I have some experience in programming using gcc and g++.

Can somebody please give some head start for getting in the groove of Borland C++ programming.

Thanks for your time,

---

### Post by ofek on 2006-02-01
Borland c++ is very similar to ms visual c++.
I'm not sure if theres any real linux program that can do the borland job although the compiler are pretty close, the graphic interface is not aviable for linux. I don't know on graphical interface for linux that is similar to borland enough to replace it.
You could probably install Borland c++ with crossover but it costs money and i'm not sure ull be able to run the program on linux to check them... i think the best thing u can do is to work in windows in a virtual machine in linux (vmware should do pretty easly) or you can just dua boot linux and windows and for borland programming go to windows. I know my suggestions aren't so optimistics but I realy can't see how to program for windows on linux... I hope somone will prove me wrong.

---

### Post by toojays on 2006-02-01
Grr. The above answer isn't very clear.

Borland and GCC both comply with the ISO C++ standard, if you want them to. If you code for the standard, your code will work under both compilers, and the only thing where you will have to duplicate work is in your project setup. That is, you will have a makefile for GCC, and a Borland project for BCC.

The incompatiblity may come if you are doing GUI work and need to use a graphical toolkit. For instance, if you needed to use MFC, you would be SOL. The last time I made a project in BCC, I was using a Borland toolkit called OWL, which is not compatible with GNU. But if you were using wxWidgets or Qt, you would be fine. Also (maybe surprisingly), if you are using straight Windows API calls you will generally be fine, because you can use winegcc.

---

### Post by slavik on 2006-02-01
don't forget gtk

---

### Post by David Marrs on 2006-02-02
[QUOTE=slavik]don't forget gtk[/QUOTE]
I was just about to say, the version of Borland I have supports GTK+.

---

