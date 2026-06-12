---
title: "Gambas Help Plz"
date: 2007-09-03
forum: Programming Talk
---

### Post by ash_td on 2007-09-03
[SIZE="2"][SIZE="3"]i made a small application in gambas

how can i run that application in ubuntu
i want to make a stand alone file.
and i made a tar file of that application
now how to install dat file

help plz[/SIZE][/SIZE]

---

### Post by pmasiar on 2007-09-03
Gambas is a kind of BASIC? Are you beginning programmer and picked Gambas because you thought it will be easy to learn?

---

### Post by pmasiar on 2007-09-05
I got private reply from OP. I did used BASIC years ago, but I don't use Gambas, and don't plan to learn it any time soon, so..

Continuing with time-proven tradition of forwarding all unsolicited private questions into appropriate public form :twisted: , I posted it here:

> well im a beginner programmer for ubuntu not for windows.

and yes i picked gambas becoz i thot it might be easy to develop programs for linux not for learning

As you just found, Gambas community is not very strong. You may have more luck with help on forum/mailing list dedicated to gambas, if they have any (I have no idea - google is your friend). But Gambas is small niche player, and as long as it will be constrained to BASIC ideas, will remain obsolete and small. Possibly a fun hobby project, but waste of time anyways :-)

I would strongly recommend you to learn more mainstream and modern language, like Python. Widely used, popular, modern, loads of tools, libraries, vibrant community, cool projects... what not to like? Wiki in my sig will get you started.

Does someone around use gambas and has better advice?

---

### Post by hammer v2 on 2008-02-11
I think, you're supposed to package it using the packaging tool. That'll will put the executable inside a deb file and sort out all the dependancies for you.

p.s  gambas 2 is released....

Installation (as root or using sudo):

1) Add the following line to your /etc/apt/sources.list file:
For Gutsy systems:

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) gutsy main

For Feisty systems:

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) feisty main


For Edgy or Guadalinex V4 and V4.1 systems:

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) edgy main



2) Update your packages sources:

apt-get update


3) Install gambas:

apt-get install gambas2

---

### Post by anantshri on 2008-03-27
well my thinking on this topic is slightly differenet.

gambas although have simmilar apporach to that of vb but still its a RAD on its own.

and hence you can't call it obslete just coz of this.

also for the working on gambas i think there is a package / compilation option you will get executable out of it.

do check it.

---

### Post by Kadrus on 2008-03-27
wow..this thread is old:p...but as you said there is a compilation option for it..and Gambas is a bit different than Visual Basic and better...as it was developed because VB had a lot of bad things..

---

### Post by nelsonhoover on 2010-06-09
One place you might try is a Gambas forum I run at [http://www.gambasforum.com]("http://www.gambasforum.com/")

---

