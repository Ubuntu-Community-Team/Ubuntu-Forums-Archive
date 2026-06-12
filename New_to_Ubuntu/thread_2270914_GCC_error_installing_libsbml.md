---
title: "GCC error installing libsbml"
date: 2015-03-26
forum: New to Ubuntu
---

### Post by Miche on 2015-03-26
[COLOR=#000000][FONT=times new roman]Hi all, [/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I am trying to install 'lisbml' via pip in Ubuntu 14.04, however I am always getting this error: [/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]>  ./base/sbml/common/libsbml-version.cpp:55:19: fatal error: bzlib.h: No such file or directory[/FONT][/COLOR]> 
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR][COLOR=#000000][FONT=times new roman]#include <bzlib.h>[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]                   ^[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]compilation terminated.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]error: command 'x86_64-linux-gnu-gcc' failed with exit status 1[/FONT][/COLOR]

The command generating the error is: 

[COLOR=#000000][FONT=times new roman]```
sudo pip install python-libsbml 
```[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Can anyone please help me? Thanks, [/FONT][/COLOR]


[COLOR=#000000][FONT=times new roman]Michele
[/FONT][/COLOR]

---

### Post by dino99 on 2015-03-26
is that header  (bzlib.h) can be found on your system with nautilus 'search' feature for example ?
are the 'pip' 'recommends' packages installed ?

but libsbml is no longer an ubuntu package ([https://launchpad.net/ubuntu/+source/libsbml](https://launchpad.net/ubuntu/+source/libsbml)) and it has 2 open bugs

an old howto was available: [http://pysces.blogspot.fr/2014/08/installing-libsbml-python-bindings-on.html](http://pysces.blogspot.fr/2014/08/installing-libsbml-python-bindings-on.html)

so the question is: where have you found that package ?

---

### Post by mc4man on 2015-03-26
It's provided by  - 
libbz2-dev

---

### Post by Miche on 2015-03-26
[COLOR=#000000][FONT=times new roman]Hello 9d9, [/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Thanks for your reply. [/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I googled the error and (as normal) I installed tons of packages which did not solve the error. There was [this tread ]("http://ubuntuforums.org/showthread.php?t=1921721")that solved the issue. Now the next error is: 
> unable to execute 'c++': No such file or directoryerror: command 'c++' failed with exit status 1

Will do some more Googling. 

RE the package libsbml, it is a rather fundamental tool to read/write SBML models into COBRA (ie a collection of Python scripts to model cellular metabolism). Github [here]("https://github.com/opencobra/cobrapy/blob/master/INSTALL.md").  

Until the next error... :)




[/FONT][/COLOR]

---

### Post by Miche on 2015-03-26
Thanks everyone for the help. Installed G++ and all went smooth.

---

