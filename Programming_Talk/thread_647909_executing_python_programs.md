---
title: "executing python programs"
date: 2007-12-22
forum: Programming Talk
---

### Post by kool_kat_os on 2007-12-22
I just wrote a program on python, how do I make it so I can make it like an actual program? (like firefox, thunderbird, yahoo messenger) or is that possible?

---

### Post by jflaker on 2007-12-22
Right click the file and go to the permissions tab and tick the "Allow executing file as program".

you should now be able to run it........

---

### Post by kool_kat_os on 2007-12-22
what extension do i save it as?

---

### Post by jflaker on 2007-12-22
It doesn't need to have an extension.....the header in the file (#!/bin/sh  <--as an example) will tell Linux how to execute the program.

---

### Post by LaRoza on 2007-12-22
> **kool_kat_os said:**
> what extension do i save it as?

In Windows, .py is used for the association, but you don't really need a file extension. .py is the standard.

Mark it as executable.

Add this line to the top:

```

#! /usr/bin/python

```

You can run it like a regular program now.

---

### Post by kool_kat_os on 2007-12-22
uhhh,
Here is a simple thing i wrote with python on windows:

```
temprature = input("what is the temp of food?")
what is the temp of food?50
>>> if temprature > 50:
	print "cooked"
else:
	print "cook more"

cooked

```

What so i save it as and how do i execute in windows?

---

### Post by jflaker on 2007-12-22
for Windows, you would need to have Python installed.......given that it is installed......save the file as .py......Windows will associate the file with the proper programs and it will execute.

---

### Post by kool_kat_os on 2007-12-22
i saved it as .py, how do i execute it without python?

---

### Post by LaRoza on 2007-12-23
> **kool_kat_os said:**
> i saved it as .py, how do i execute it without python?

What?

You can't run a Python script without Python.

---

### Post by CptPicard on 2007-12-23
> **kool_kat_os said:**
> i saved it as .py, how do i execute it without python?

On Windows, check out py2exe, but... that's really not neccessarily the point you know... your Python programs *are* "real programs". Interpreted/VM languages are going to be more and more common in the future...

---

### Post by pmasiar on 2007-12-28
On Windows, you can associate python.exe with .py extension, so clicking on file name in Windows Exploder will execute the file. It has same functionality as shebang line in Linux (#! /usr/bin/python) - to tell computer how to "understand" the code.

It will run in text mode (terminal), to make it pretty GUI as Firefox is, you need to  work more on it. EasyGUI is the simplest GUI library AFAIK.

---

