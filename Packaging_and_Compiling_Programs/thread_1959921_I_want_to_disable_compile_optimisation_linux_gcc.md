---
title: "I want to disable compile optimisation linux gcc"
date: 2012-04-16
forum: Packaging and Compiling Programs
---

### Post by forsubhi on 2012-04-16
I don't know if this forums accept programming Question , so if one know please tell me that 

I want to disable compile optimisation in  linux gcc compiler and then debug that code with eclipse cdt , any one know how to do that ?

---

### Post by lovinglinux on 2012-04-16
Moved to Packaging and Compiling Programs

---

### Post by r-senior on 2012-04-16
The option to pass to gcc is '-O0'. That's minus, capital-O, zero. But that's the default for gcc anyway, unless the build settings in Eclipse overrride it with -O1, -O2, etc.

---

### Post by forsubhi on 2012-04-16
I have imported my project in eclipse using new --> make file project from existing resource 

so I have Question , DO I have to go to make file and edit it or go to eclipse and then to project properties .

My project is SphinxTrain which  is open source project available at 
[http://sourceforge.net/projects/cmusphinx/files/sphinxtrain/1.0.7/](http://sourceforge.net/projects/cmusphinx/files/sphinxtrain/1.0.7/)

---

### Post by r-senior on 2012-04-17
In that case, the setting is probably in the Makefile. 

If it's using GNU autotools be careful where you make the change because the Makefile may be generated. You'll know it is if you have configure.in, Makefile.am, etc.

---

### Post by forsubhi on 2012-04-18
thamks r-senior I use 
configure CFLAG '-O0' CXXFLAF '-O0' , and the optimisation become less than before , but I still have the following problems 

[http://ubuntuforums.org/showthread.php?t=1960624](http://ubuntuforums.org/showthread.php?t=1960624)

please help me

---

### Post by bregma on 2012-04-18
> **forsubhi said:**
>  
configure CFLAG '-O0' CXXFLAF '-O0' 
That should be [FONT="Courier New"]./configure CFLAGS='-O0 -ggdb3' CXXFLAGS='-O0 -ggdb3'[/FONT] and make sure there is no space around the '[FONT="Courier New"]=[/FONT]'.  Make sure you do a full rebuild after this ([FONT="Courier New"]make clean; make[/FONT]).

---

### Post by forsubhi on 2012-04-18
oh sorry this is the command that I used 
```

./configure CXXFLAGS='-g -O0' CFLAGS='-g -O0'
```
what is the difference between  this command and  
```

[FONT=Courier New]./configure CFLAGS='-O0 -ggdb3' CXXFLAGS='-O0 -ggdb3'[/FONT] 
```note : I choose linux GCC from toolchain when I make project with eclipse

---

### Post by forsubhi on 2012-04-18
I use ```
 [FONT=Courier New]./configure CFLAGS='-O0 -ggdb3' CXXFLAGS='-O0 -ggdb3'[/FONT]
```
but I still see variable without values and eclipse show me optimized out , it there any additional steps to do in eclipse?

---

### Post by MadCow108 on 2012-04-19
please don't open two threads on the same subject, the answer has been posted here:
[http://ubuntuforums.org/showthread.php?t=1961086](http://ubuntuforums.org/showthread.php?t=1961086)

---

### Post by forsubhi on 2012-04-20
thank you MadCow108

---

