---
title: "How WPF Application EXE Run in Ubuntu?????"
date: 2011-05-17
forum: Programming Talk
---

### Post by Girish Kapoor on 2011-05-17
Hello Guys,
                I am new in Ubuntu and i have not much experience in ubuntu, i want to run my wpf application exe in ubuntu. I am created this application in visual studio 2008 in Windows7 and now i want to running ubuntu 11.04 linux. Please can anyone help me asap.

---

### Post by NovaAesa on 2011-05-17
What language is the program written in?

I can see two options:

1) Try to compile the program under Linux. If you wrote platform independent code, this shouldn't be too much of a challenge.

2) Compile under Windows and then run in Linux using Wine.

EDIT: I just looked up what WPF stands for. It doesn't look very cross platform to me... Wine might be the best approach.

---

### Post by Girish Kapoor on 2011-05-17
Hello NovaAesa,
                         I have written the code in .net language of wpf application

---

### Post by johnl on 2011-05-17
WPF is part of .NET, which can be run (mostly) by using [mono](http://www.mono-project.com).  **However**, from the mono page on [WPF](http://www.mono-project.com/WPF):

> 
[B]At this point, no group in the Mono project has plans to implement Windows Presentation Foundation APIs as part of the project.
[/B]

We do not have any plans because the project is too large and there has not been any serious interest from the community to make this effort move forward. 


So you are out of luck there, it looks like.

It might be possible to install .NET runtime inside of Wine and run your program that way, but it sounds dubious to me.

---

