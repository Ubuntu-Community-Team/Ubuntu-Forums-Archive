---
title: "How to get started with linux programming?"
date: 2014-04-16
forum: Programming Talk
---

### Post by SuperMiguel on 2014-04-16
So i been a Linux user for many years, and im also a software engineer student, i like programming but i have hard time setting goals for my self, so in order to improve my programming skills i want to help the Linux community but i have no idea how to get started.. Can you guys provide me with few tips?

---

### Post by Dreamer Fithp Apprentice on 2014-04-16
Pick any project that appeals to you and go to their website. Volunteer. Any level of ability or set of skills you have there's probably plenty of projects that could give you an appropiate assignment. Just tell then what you want. If you are proficient with some higher level language you might look for projects in which it is used.

---

### Post by coldraven on 2014-04-16
You could write a tutorial or article and publish it on a blog or perhaps for this magazine [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
They did a whole series on Python that you can still download  from here: [http://fullcirclemagazine.org/python-special-edition-volume-six/](http://fullcirclemagazine.org/python-special-edition-volume-six/)
Just change the number in the link to get volumes one to five.

---

### Post by SuperMiguel on 2014-04-16
> **Dreamer Fithp Apprentice said:**
> Pick any project that appeals to you and go to their website. Volunteer. Any level of ability or set of skills you have there's probably plenty of projects that could give you an appropiate assignment. Just tell then what you want. If you are proficient with some higher level language you might look for projects in which it is used.

ya but how would i know what needs to be fix? can you recommend something easy just to get stared?

---

### Post by mörgæs on 2014-04-16
First of all, are you experienced in tweaking and compiling on your own computer?

---

### Post by SuperMiguel on 2014-04-16
> **mörgæs said:**
> First of all, are you experienced in tweaking and compiling on your own computer?

yup

---

### Post by mörgæs on 2014-04-16
Here's a bug that could be suitable as a first project:
[https://bugs.launchpad.net/ubuntu/+source/gpicview/+bug/1022265](https://bugs.launchpad.net/ubuntu/+source/gpicview/+bug/1022265)

---

### Post by tux3do on 2014-04-16
In the console:

gcc - C compiler
g++ -  C++ compiler
java - javac / eclipse / netbeans is supported
python - python interpreter
php - php interpreter

To compile and run  a C program
> 
gcc hello.c -o hello
./hello


To compile and run a C++ program
> 
g++ hello.cpp -o hello
./hello


Depending on your preference and skills pick the language of choice :)  Get some libraries, for example libsdl  and have some fun :popcorn:



To run python program
> 
python hello.py


To run php program
> 
php hello.php


---

### Post by SuperMiguel on 2014-04-16
> **mörgæs said:**
> Here's a bug that could be suitable as a first project:
[https://bugs.launchpad.net/ubuntu/+source/gpicview/+bug/1022265](https://bugs.launchpad.net/ubuntu/+source/gpicview/+bug/1022265)

ok how would i start? like where do i get the source code?

bzr branch lp:ubuntu/gpicview ?

---

### Post by mörgæs on 2014-04-16
I don't code myself (not in Buntu context at least) so I wouldn't know. 
I just thought it looked like a nice, isolated task without a long dependency tree.

---

