---
title: "Advice Needed (MySQL / Which Language?)"
date: 2007-11-06
forum: Programming Talk
---

### Post by dhtseany on 2007-11-06
Hey everyone,

I need to write an application to mainly run on Windows XP and 2K. I need to be able to query a MySQL database and do simple INSERT, DELETE, etc commands.

I know I need ODBC and I already have it installed and running.

I'm pretty good with PHP but the people I work for don't want to work out of IE or FF all day so they've tasked me with writing this thing.

I've looked into VB6 and it looks OK but the coding behind it is like a big blur to me.

Any other suggestions or places I can get a little better understanding of VB6?

Thanks in advance,

Sean

---

### Post by dburnett77 on 2007-11-06
Stick to OS==Windows.  This is a Linux forum.  Last I checked.

If, converted, you want to Samba out, then run an Apache server.  Dumb...

---

### Post by dhtseany on 2007-11-06
Hey *******,

This section of the forum is independent of OS. I'm running 13 Ubuntu servers and a whole assortment of Ubuntu desktops. However, sometimes your 60y/0 boss wants his fun little Windows XP box.

Thanks for such an outstanding waste of my time.

I'll remember next time you ask for advice and drop stupid comments to you.

Anyone without their head up their butt have a suggestion?

---

### Post by Siph0n on 2007-11-06
lol This forum isn't only for ubuntu ;) What about Python to interact with the database? I remember seeing a lot of people doing that on the forums...

---

### Post by dhtseany on 2007-11-06
Hey thanks for the intelligent response :)

Anyways, will Python run on XP?

---

### Post by pmasiar on 2007-11-06
Python will run on XP with no problems - install from ActiveState, their Python is better on Win than stock Py from Python.org.

Or if you are adventurous and want access to .NET also, look at IronPython. Classic Python, (CPython) is build on top on C libraries, some have problems on Win. IronPython is build on top of C# and .NET, so most .NET libraries are fine but some C libraries are not. IronPython was released under MS-specific license, but was recognized as "open" by OSI.

wxPython is nice GUI (for CPython).

---

### Post by timcredible on 2007-11-06
python.

---

### Post by dhtseany on 2007-11-06
Now will Python let me do some visual stuff as well like VB does? 

I guess to clarify what I need:

- I need the ability to visually design what is seen on the GUI

- The code needs to be rather easy to learn

- Easy to connect and interact with MySQL (Like PHP only must be a stand alone app [.exe-ish])

---

### Post by dhtseany on 2007-11-06
*bump

---

### Post by ankursethi on 2007-11-06
If you use GTK+ libraries for designing the GUI, you can go with the GLADE interface designer. If you go with Tkinter, you'll have to code the thing by hand.

You'll have to run your Python programs using an interpreter, like Java applications (only with Java one first compiles the app to bytecode, while with Python one *usually* runs them as they are). A Py2EXE thingy is available that translates Python to native EXEs but I don't know how effective that is.

Yup, Python connects to MySQL easily. Dunno about ODBC, I've never looked into databases.

Python syntax is very easy to learn. If you know C/C++/Java, Python will take you a weekend to learn (complete with GUI and MySQL stuff).

---

### Post by slavik on 2007-11-06
gtk+, libglade, C/C++/Perl/Python ... you get the added benefit of it being not painful when moving to a different OS if you need to. :)

---

### Post by smartbei on 2007-11-06
Hello dhtseany,
[I hope that website turned out alright]

To repeat what other's have said, I would go with Python, and unless you are doing something very windows-specific I would go with normal CPython, and not IronPython, so that it is easier to get help from forums (such as this one) where everyone is on Linux (This might not be all that important, others should feel free to correct me).

From my experiance building gui's (admittedly, small), if you are doing something simple I would recommend going with Tkinter. I found it much simpler to code everything by hand than to design using one of the various Glades.

Py2EXE works well, and I definately recommend that you use it so that your python app work more natively (It will look the same, but people are used to .exes and don't want to download 20mb of python) on windows.

What, if I may ask, is the goal of the application?

---

### Post by LaRoza on 2007-11-06
> **smartbei said:**
> 
To repeat what other's have said, I would go with Python, and unless you are doing something very windows-specific I would go with normal CPython, and not IronPython, so that it is easier to get help from forums (such as this one) where everyone is on Linux (This might not be all that important, others should feel free to correct me).

From my experiance building gui's (admittedly, small), if you are doing something simple I would recommend going with Tkinter. I found it much simpler to code everything by hand than to design using one of the various Glades.



I was going to recommend Python also, but I see others have already done so, so I will not.

Not everyone is on Linux, all the time, but Python is the same on different platforms, so your advice to use CPython is good. 

Tkinter is a simple Graphics library, and comes part of ActivePython, so it will be easy to use. However, wxPython is in many ways better. There is an installer for Windows, check my wiki for the links.

---

