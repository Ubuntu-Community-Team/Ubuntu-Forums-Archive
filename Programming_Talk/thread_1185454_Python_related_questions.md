---
title: "Python related questions"
date: 2009-06-12
forum: Programming Talk
---

### Post by superpink99 on 2009-06-12
im creating my first application and ive come across some problems:

1. how do i reset an application? My objective is that when i click a reset button the application resets as if its like a newly opened application.
ex. when i typed in stuffs on a input frame, when i click reset it erases all that i typed

2. what is the script for getting the inputs of user on an input frame?
my objective is that when a user types in her name and press ok, i get to store/display her input on another frame/panel.

thanks..........

---

### Post by Tony Flury on 2009-06-12
> **superpink99 said:**
> im creating my first application and ive come across some problems:

1. how do i reset an application? My objective is that when i click a reset button the application resets as if its like a newly opened application.
ex. when i typed in stuffs on a input frame, when i click reset it erases all that i typed

Resetting an application back to it's starting state (without stopping and restarting it) really does depend on what your application does and what you want to reset - just the data on the form being displayed or do you also for instance want to undo any changes that the application made to files for instance ? There is no generic method for resetting an application, you (as the application writer) have to decide what "reset" actually means for your application. The problem is the same if you use Python or any other high level language - although there are a few that have a reset, that reset is limited and can't undo side effects like files written to, or graphics drawn.

A simple way (possibly) to achieve a reset would be to enscapsulate all the application logic in a class, and run the application by calling a method of the class from a "main" file. The reset would then cause the class to exit that method, and the "main" could delete the class instance and re-create it from scratch - however you would have to be careful to ensure that your class destructor removes everything you need it to, as you could end up with orphaned windows etc.

> **superpink99 said:**
> 
2. what is the script for getting the inputs of user on an input frame?
my objective is that when a user types in her name and press ok, i get to store/display her input on another frame/panel.

thanks..........
That all depends how you are constructing your input and output frames. if you are using GTK then the Text widget has a "get_text" method so your application can retrieve what the user typed, and similarly has a "set_text" method so your application can set the text into that widget. I would expect other GUI frameworks (TCK, KDE etc) to be similar. Again this is not specific to python.

---

### Post by superpink99 on 2009-06-12
Yes sorry i did not specify things Tony Flury:

for the first one what is **just the data being displayed**

and for the second one im using **wxpython** for my GUI, for the wxpython i think it uses GetValue, the problem is that im having trouble using it.

---

### Post by Tony Flury on 2009-06-13
In python, the best way of doing what you want is to explicity code to reset your windows and applications, either by destroying the classes and starting again, or at least by reseting the values you need to reset - there is no single command to do what you want.

With regards to your wxpython problem - i can't help you - as I use GTK - if you post your exact question to this forum - maybe with the title of "problems with wxpython GetValue" (or something similar), you are more likely to get someone to answer it with some helpful information.

---

