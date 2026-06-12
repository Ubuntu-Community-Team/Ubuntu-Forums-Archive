---
title: "run a script from inside c program"
date: 2010-06-22
forum: Programming Talk
---

### Post by miak on 2010-06-22
Hi,

I am writing a GUI in C that will be communicating with the software written in python.
I basically want to call different functions from outside of the GUI whenever a button is pressed on the GUI, i think this should be relatively easy to do(just run a command in the terminal will do it). 
A tougher problem for me is to combine GUI and python application, i.e. to display data on the GUI whenever my python application has processed the data. I was thinking of storing data to a file and then opening the file from the GUI, but I don't know how to send signals from the python application to the GUI written in C, any ideas???

Any ideas will work, even if they will give me some more info that i can google easier.

Also anyone has any idea how to create plots with GTK+, or should I switch to some other tool for writing application. I want to write my GUI in C because it seems to be more stable then GUIs written in python.

Thanks in advance,
miak

---

### Post by Yarui on 2010-06-22
I don't remember how to do it, but I made a C++ program years ago that used the windows command line to perform a few actions.  It wasn't difficult to do at all, it used an extremely standard C++ function.  I'm not sure if that is something that C does the same way, but I'm sure it is completely doable in linux as well as windows.  I'm not sure, however, how to make python send information to your C program.  I was recently reading up on a standard linux program called inotify that you can use to tell programs when files change.  You may be able to make the C program use inotify to detect when the python program has made changes to the file you mentioned.

---

### Post by slavik on 2010-06-22
why not write a gui in python? gtk/qt/tk are all available.

---

### Post by miak on 2010-06-23
I already wrote a GUI in python, but it just isn't very stable, I am regularly updating plots on the GUI and after a while, 15 minutes the GUI freezes and the only option is to shut it down. Basically my program is very resource consuming that's why I'm trying to optimize it by writing a C GUI, and in general GUIs with python don't seem to work as well as they are supposed to. 
Is there any way to update something in /proc/* directory so that the process knows something happened?

---

