---
title: "using GCC for multiple files"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by MaWiSo on 2013-05-09
I'm a beginner to using gcc in command line
[COLOR=#000000][FONT=verdana]I have a project with multiple .h and .cpp files.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I want to compile this project and add #defines in the compilation command in gcc.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]some of the .h files are paired with .cpp files.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]some are just standalone.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]each .h file has its own #define that needs to be set[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]how to do this ??[/FONT][/COLOR]

---

### Post by codemaniac on 2013-05-09
this is where 'make' utility comes into picture and makes life easier.

the documentation is a bit fat but worth a read to master this great utility.

[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

---

