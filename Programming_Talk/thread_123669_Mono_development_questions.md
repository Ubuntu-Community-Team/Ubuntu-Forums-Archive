---
title: "Mono development questions"
date: 2006-01-30
forum: Programming Talk
---

### Post by rama on 2006-01-30
I am interested in creating an application in C# and I thought of trying out mono. Since the computer I am going to install it runs windows, will I be able to write, and test the application using ubuntu and then install .net framework and my application on the other pc?
I 'd like to avoid using gtk, but if I do use it, how tough will it be to convert all the objects and methods to system.forms objects and then recompile the application for deployment?

---

### Post by sas on 2006-02-02
As things stand at the minute I believe it'd  be a total rewrite of all or most of the GUI code. You can install GTK on windows though, if you do that you don't even need to recompile, just copy and pasting the program will work.

---

### Post by Metz on 2006-02-02
I tried that....writing first using System.Forms on Win....then had to rewrite when ported to Linux. Everytime I made a change....I had to port the change to GDK. In the end, I got bored with the whole process....and just installed GTK# on Win....and stuck with one stream !!! :)

---

