---
title: "What language to use for..... GUI for microcontroller"
date: 2009-11-19
forum: Programming Talk
---

### Post by stefanst on 2009-11-19
Hi Everybody,

I don't want to start the holy war of "which is the best language" here, but I could use a personal recommendation. Here is my task:

- Run home heating and cooling system with multiple zones from an ARDUINO prototyping microcontroller
- Create a GUI for communication and parameter setting for the ARDUINO (comm via USB or serial)

Features:
- Send paramters via serial or USB
- receive temperature data via serial or USB
- log data either in textfile or mysql
- Cross-platform would be nice. Development on WinXP, then deploy to small Ubuntu box

My experience:
- back in the 80s: several BASIC dialects, Assembly, Fortran
- more recently: MicroSoft VB for Apps (Access, Excel)
- also created some .asp pages talking to an MS SQL server with the absolutely lovely old version of MicroSoft's Visual Studio from 1998 or so.

So my OO programming skills are not the greatest, but at least I have some experience. The "C" languages scare me a bit - all them-there brackets and such seem tedious.

I looked into "Processing" from [www.processing.org](www.processing.org) a bit since some Arduino projects use it, but it seems not very well suited for generating GUIs.

My needs for this project are not too demanding and the closer the language is to what I already know the happier I would be.

From what I have learned so far, PYTHON seems the #1 candidate, but maybe there is a terribly simple solution that I have completely overlooked - like "GUIs 'R us"....

Any input is welcome - and remember: I'm scared of brackets ;-)

Stefan

---

### Post by CptPicard on 2009-11-19
As long as you can get the communication to work, Python. The show-stopper in crossplatformness may be any C module you may have to write for that part of the application.

---

### Post by ZeroSpawn on 2009-11-19
> **stefanst said:**
> 
Features:
- Send paramters via serial or USB
- receive temperature data via serial or USB
- log data either in textfile or mysql
- Cross-platform would be nice. Development on WinXP, then deploy to small Ubuntu box


Mmm to get those features you are looking at using C++. If you want full usage of MySQL you may have to use the OO programming. But thats from my experience, had a class project to interface a SQL with self made window (GUI) and the only I could do it was with OO.

Dont be scared of C++ just pick up a book and you will find out how much quicker you can write code. You can take 55 line of Assembly and reduce it to 10 lines in C++.

[My Engineering Hobbie Site]("http://home.comcast.net/%7Ezerospawn/") :KS

---

### Post by Can+~ on 2009-11-19
> **stefanst said:**
> - Send paramters via serial or USB
- receive temperature data via serial or USB

I think [pySerial]("http://ubuntuforums.org/showthread.php?t=1235241") does that, otherwise, you could open it as a file (I love that from *nix)

> **stefanst said:**
> - log data either in textfile or mysql

"logger" module, "sqlite3" for portable database (both are part of the standard library).

As for the GUI, pick your poison: pyQT, pyGTK, wxPython, tk (this one is standard).

> **ZeroSpawn said:**
> Mmm to get those features you are looking at using C++. If you want full usage of MySQL you may have to use the OO programming. But thats from my experience, had a class project to interface a SQL with self made window (GUI) and the only I could do it was with OO.

You should be hacking the gibson, ZeroCool.

---

### Post by wolterh on 2009-11-20
I think that if you want simple and cross-platform then you're looking at python. I would recommend C, but you already said you were scared of it; however, C is much simpler than assembly..

---

### Post by CptPicard on 2009-11-20
Do I see serious suggestions that the guy might be doing this in assembly, and therefore he should be using something because it is "higher level than assembly"? :)

Do note that it seems to me like the microcontroller itself is communicated through a serial/usb port, not programmed straight on hardware...

---

### Post by stefanst on 2009-11-20
> **CptPicard said:**
> Do I see serious suggestions that the guy might be doing this in assembly, and therefore he should be using something because it is "higher level than assembly"? :)

Do note that it seems to me like the microcontroller itself is communicated through a serial/usb port, not programmed straight on hardware...

Right you are!

I just mentioned experience in assembly to be complete - but this is NOT an experience I would like to repeat. And it was more than 20 years ago when I still had most of my braincells available.

The microcontroller will be programmed in a specifically developed rather basic-like language that is quite easy to pick up. I then just want to change parameters and log data from the GUI.

Thanks for all the suggestions!

ST

---

### Post by exutable on 2009-11-20
Funny you created this thread.

I am creating a climate control system right now for my first semester project and I created a GUI for interacting with my microcontroller... Mostly just for starting the server, telnetting to it, writing to it and reading from it.

I am also creating an interface that can control the temperature and get temperature and moisture readings.  It's VERY simple in Python and PyGTK.  I looked at PyQt but didn't really like it because it has potential for requiring licensing and pygtk is a lot easier from my short experience.

---

### Post by stefanst on 2009-11-21
> **exutable said:**
> Funny you created this thread.

I am creating a climate control system right now for my first semester project and I created a GUI for interacting with my microcontroller... Mostly just for starting the server, telnetting to it, writing to it and reading from it.

I am also creating an interface that can control the temperature and get temperature and moisture readings.  It's VERY simple in Python and PyGTK.  I looked at PyQt but didn't really like it because it has potential for requiring licensing and pygtk is a lot easier from my short experience.

Would you mind sharing code, schematics, plans? I don't always insist on re-inventing the wheel, when there is a perfectly serviceable wheel available :D

ST

---

### Post by maximinus_uk on 2009-11-21
> **ZeroSpawn said:**
> Dont be scared of C++ just pick up a book and you will find out how much quicker you can write code. You can take 55 line of Assembly and reduce it to 10 lines in C++.

Don't be scared of python: those 10 lines of C++ are probably 4 lines of python. (Maybe only 2 lines of Lisp, but thats another thing).

Seriously, the hardest part will be in the communication code. If you can get that working in python, you'll find that MUCH easier to deal with than C++.

C++ is, in general, not a good language (and I speak as a old fan of C).

---

### Post by exutable on 2009-11-21
Well, the climate control system we're still working on... We got the analog to digital conversion down and can get a temperature reading.  As for the GUI, we're using a web interface, so I haven't created the Python GUI yet.

As for coding for the microcontroller, the "IDE" for making, connect, writing and read from it is right here.  It's no where near complete but is fully functional.

The attached picture shows it in action.  I couldn't start the server or connect via telnet because I was testing the app and left a rogue telnet connection, it completely screws it up and you have to restart or logout and back in.  Long story short, it works.

---

### Post by stefanst on 2009-12-07
Alright - I started learning C. Just "C" with no additions :-)
As it turns out, the MC is programmed in a C dialect anyway, so I might as well.

So far so good. the "{}" and "[]" on my keyboard got more use in the last two weeks than the previous 5 years combined!

Thanks,

Stefan

---

