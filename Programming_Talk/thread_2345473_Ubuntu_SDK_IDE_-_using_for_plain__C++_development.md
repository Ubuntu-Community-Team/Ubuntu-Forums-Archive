---
title: "Ubuntu SDK IDE - using for plain  C++ development ?"
date: 2016-12-04
forum: Programming Talk
---

### Post by Vaclav Vasek on 2016-12-04
Could somebody give me a **hint how to navigate** Ubuntu SDK IDE to add #include(s) and libraries to plain C++ application?
I cannot even find what compiler is used. 
The SDK has bunch of build in resources , but it is not clear how to implement them and using "Help" does not help much. 

I am after "video processing" similar to OpenCV. 

On first access I see lots QML stuff and after little search found "Hello word" example and got it running. 

Or is this SDK too advanced for beginner to run JUST C++? 

Second question - is there a dedicated forum for Ubuntu SDK IDE ?
I do not see one on this site. 
Quite by accident I accessed some SDK development side and I am sure that is not the place to ask for help. 

Any help will  be appreciated, even "Google it ". 
Cheers

---

### Post by karl96 on 2016-12-05
Hi, no idea if you have found it yet but I will answer it just incase, or if anyone else is having similar issues.

You can see the compiler by clicking (on the menu):
tools then options then build & run then compilers. It'll probably show GCC (G++ is actually the C++ compiler).

In order to use libraries you'll have to use the linker. The "" tells the preprocessor to search the path specified by the -l flag, you can do it manually or by right clicking on the project, clicking add library, and then selecting where the library is (it'll end in .so), header files are (usually) contained in /usr/include and libraries in /lib (or related files, lib64, /usr/lib, etc).

You will need to install the corresponding dev packages of the libraries you want to use if they're not already installed.

You can also tell bash to tell you what libraries binaries require, e.g from the terminal:
```
ldd /bin/bash
```
Will show you what libraries the bash executable requires :)

If you need any more help just message me and i'll see what I can do.

---

### Post by cariboo on 2016-12-05
Moved to Programming.

---

