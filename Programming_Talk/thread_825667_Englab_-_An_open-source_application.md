---
title: "Englab - An open-source application"
date: 2008-06-11
forum: Programming Talk
---

### Post by sg_aurelius on 2008-06-11
We are pleased to inform you that the release 0.2alpha edition of the open-source program has been published. 
 
Our site is located to [http://englab.sourceforge.net](http://englab.sourceforge.net)  . You can download it from  [https://sourceforge.net/project/showfiles.php?group_id=206384](https://sourceforge.net/project/showfiles.php?group_id=206384)
 
 EngLab is a cross-compile mathematical platform with a C like syntax, intended to be used both by engineers and users with small programming knowledge. The initiative has been taken from a group of students a year ago. 
 
Our goal is to develop an easy-to-use computaion and simulation platform with a C++ like syntax. We have adopted Matlab's structure philoshophy and C++ 's structured language syntax. There are various toolboxes (packages of functions relative to a certain scientific field), which depend on open-source libraries. 
 
The EngLab distribution is available in two ways: there are two basic Englab releases, EngLab Console and EngLab GUI. EngLab Console allows EngLab's execution through the consolse(Linux or Windows). EngLab GUI gives the opportunity of using EngLab through a graphical user interface. EngLab GUI is implemented the open-source library wxWidgets 2.8, providing additional usability compared to EngLab Console edition. EngLab GUI is independent, so there is no need for EngLab Console to be installed, in order to properly install and execute EngLab GUI. 
 
Toolboxes are distributed as seperate packages. Their installation is possible either through EngLab Console or EngLab GUI. The reason is that those toolboxes depend on open-source libraries that have to be previously installed. So as the user not to be forced to install those libraries directly, user can install packages and toolboxes at his/her own will. 
 
For the tim being, EngLab Console edition is available for Windows and Linux and Englab GUI is available for Linux. 
 
Until now EngLab has the following features : 
 
- 16 types of variable declaration (int, float, ...) 
- Variables declaration with limitless number of dimensions. 
- Repetition structures (for, while, ...) 
- Arithmetic, logical and binary operations 
- Constant number declaration (pi, phi, ...) 
- Graphical manipulation of variable values of any dimension (Englab GUI) 
- Adjustable graphical environment (Englab GUI) 
- Editor for writing *.eng functions (Englab GUI) 
- Command history for the last 5 sessions 
- Immediate access to variables, constants and functions (EngLab GUI) 
- Recent files opened through EngLab (EngLab GUI) 
 
Toolboxes that have been fully or partially implemented: 
 
- a package containing basic functions of C (trigonemetric, hyperbolic trigonometrical, ...) 
- a package containing some statistic functions 
- a package containing functions that allow convertions of the variable type 
 
All these toolboxes accompany the basic two EngLab editions, since they do not depend on another open-source library. Moreover, some other toolboxes have been partially implemented: 
 
- a package that contains functions for the manipulation of 2-D matrices (determinant, inverse array, ...). This package depends on the open-source library NewMat10. 
- a package that contains functions for image processing. This package depends on the open-source library CImg. 
- a package that contains functions for image processing. This package depends on the open-source library OpenCV. 
 
Also, we develop 
- a toolbox for visual data representation(plots etc) 
- a toolbox that contains functins for manipulating polyonymials, root detection, computation of integrals and derivatives, special functions and more. 
 
Those two toolboxes will be available in the next releases. 
 
The disadvantage is the number of EngLab developers, which does not allow EngLab's quick development. Thus, helping us would be welcomed. 
 
You can help us with the following two ways: 
 
&#61485;	By reporting bugs, which you have observed during EngLab execution. You can report bugs in englab.sourceforge.net. Moreover, you can suggest new features that would improve EngLab's usability and performance. New features can be suggested in [https://sourceforge.net/tracker/?group_id=206384&atid=997443](https://sourceforge.net/tracker/?group_id=206384&atid=997443)
&#61485;	Suggest some new features. This can be done in
[https://sourceforge.net/tracker/?group_id=206384&atid=997446](https://sourceforge.net/tracker/?group_id=206384&atid=997446)
 
- If you would like to get more into EngLab, you could become EngLab developers and help us. That requires C++ knowledge. 
 
If you have read till here, that's a good sign. ;) 
 
You could ask questions in the mailing list [email]englab-support@lists.sourceforge.net[/email] or in the forum . 

There is online and PDF documentation. They are available in

[http://englab.sourceforge.net/documentation.html](http://englab.sourceforge.net/documentation.html)
 
EngLab development team : 
 
Bugfest development team : 
 
Serenis Charalampos - PhD student of the Department of Electrical Engineering of Aristotle University of Thessaloniki(Greece). 
Tsardoulias Emmanouil - PhD student of the Department of Electrical Engineering of Aristotle University of Thessaloniki(Greece). 
Gavves Efstratios - Dipl. Engineer of the Department of Electrical Engineering of Aristotle University of Thessaloniki(Greece). 
Parastatidis Nikolas - Postgraduate student of the Department of Electrical Engineering of Aristotle University of Thessaloniki(Greece). 
 
Also contributed: 
 
Gkekas Christos - Dipl. Engineer of the Department of Electrical Engineering of Aristotle University of Thessaloniki(Greece). 
Vogianou Thanassis - PhD student of the Department of Electrical Engineering of Aristotle University of Thessaloniki(Greece).

---

### Post by Ramses de Norre on 2008-06-11
Seems interesting but not in a usable state yet. I'll keep an eye on it though.

---

### Post by sg_aurelius on 2008-06-12
It is in alpha stage, so it is surely not in using state yet. For the time being some bug reports and features would be an ideal contribution. Therefore if anyone can help us by doing so, that would help us a lot.

---

### Post by sg_aurelius on 2008-06-12
Also, does anyone know how we can add Englab to Debian and/or Ubuntu repos?

---

