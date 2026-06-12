---
title: "How can i define a new data type in python?"
date: 2005-07-24
forum: Programming Talk
---

### Post by André on 2005-07-24
Hi everybody,

i am just starting with programming (again :-)).

Right now i would like to do the following:

1. I would like to define a new datatype. For simplicity let's call it index with index having site and word (like having a datatype with two strings site and word, where i can put this stuff).

2. I would like to put the datatype definition in a file like index.py and use this as a module

3. I would like to have a file main.py that uses the datatype from index.py.

Can i do this somehow? Or do i have to define an array with these two strings in main.py? Is it possible to have a "use"-relationship between index.py and main.py?

Hope i made my self clear :-)

Greetings and thanks for any help
André

---

### Post by Juergen on 2005-07-24
You probably should read all of this (online-) book, but for your actual problem look at this chapter:
[http://diveintopython.org/object_oriented_framework/index.html](http://diveintopython.org/object_oriented_framework/index.html)

Did you look at pythons native datatypes? Maybe a dictionary already does what you want.
If not, derive from it.

---

### Post by vintem on 2005-07-24
for me, the best book I read on python, was: "a byte of python" ([www.byteofpython.info](www.byteofpython.info)) by C H Swaroop.
It's very clear for beginners and it's free for download.
Chapter 11 focuses on Object-Oriented programming, and that's what you want to do: define your own datatypes (they're called classes).

---

### Post by André on 2005-07-25
Hi,

thanks for your answers.

First i wasn´t thinking about OO because i only wanted the datatype without any methods and stuff... but i must admit that this was pretty stupid ;-)

Maybe it was too late for me :-) It´s excactly what i need.

So, thanks again
André

---

