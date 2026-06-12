---
title: "UNdefined reference to 'cv::function_name' sous ubuntu 11.10 avec openCV 2.4.2"
date: 2012-12-15
forum: Programming Talk
---

### Post by mimya on 2012-12-15
Salam, Bonsoir

J'utilise OpenCV 2.4.2 sous ubuntu 11.10 et genom 2 ( du package robotpkg développé par le laboratoire LAAS)
J'essaye d'installer un module en utilisant make make install, dans le code du module, des fonctions de librairie OpenCV sont utilisées. À chaque référence à celles-ci j'ai l'erreur Undefined reference suivi du nom de la fonction. 
J'ai déja essayé OpenCV avec des programmes simples. Je compilait avec la commande

g++ `pkg-config --cflags opencv` my_code.cpp -o my_code `pkg-config --libs opencv

et ça fonctionne correctement.

L'enête du programme contient:
```
#include <portLib.h>
 
#include "server/targdetHeader.h"
#include <portLib.h>
#include <cv.h>
#include <highgui.h>
 
#include "/home/amina/src/openrobots/include/opencv2/imgproc/imgproc.hpp"
#include "/home/amina/src/openrobots/include/opencv2/objdetect/objdetect.hpp"
#include "/home/amina/src/openrobots/include/opencv2/highgui/highgui.hpp"
 
#include <stdio.h>
#include <h2timeLib.h>
#include <time.h>
#include <iostream>
#include <fstream>
#include <string>
 
#include <viam/viamStruct.h>
```

les variables PATH, PKGCONFIG et LD_LIBRARY_PATH sont normalement bien configuré dans les fichiers .bashrc et /etc/bash.bashrc

Toute indication est la bienvenue, merci d'avance

---

### Post by Zugzwang on 2012-12-16
Can you copy&paste the output of running the compilation process here, including the command used for actually compiling the example that you have problems with? If I get it correctly, you only pasted the compilation command that you used for your other code that you could compile correctly.

---

### Post by Lux Perpetua on 2012-12-17
"Undefined reference" is a linker error.  You may need to specify the location of your OpenCV libraries manually when you compile your package.  Depending on your package's build setup, this may or may not require modifying the makefile.  I can't really say more than that without more information...

---

### Post by mimya on 2012-12-19
Salam

FIrst, thank you for your answers
I solved the problem and I want share the answer with you.
I installed OpenCV 2.4.2 manually, the prefix installation was /usr/local/
Genom ( the tool I use) installed another version automatically, that was version 2.4.1 and the prefix was /home/amina/src/openrobots
My variables PKG_CONFIG_PATH and LD_LIBRARY_PATH included both prefexies and I was passing genom prefix to ./configure when creating makefiles: all that created a conflict when linking.
Now, I modified my environment variables to keep only one link to one version of the library, the one that genom installed.

---

