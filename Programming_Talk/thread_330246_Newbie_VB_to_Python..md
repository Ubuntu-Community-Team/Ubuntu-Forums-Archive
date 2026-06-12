---
title: "Newbie: VB to Python."
date: 2007-01-02
forum: Programming Talk
---

### Post by zornan on 2007-01-02
I was relatively a beginner on Visual Basic when i made the switch to Linux. I love linux but want to learn how to program on it. I've been reading about Python and have found that there are a lot of language similarities. But what i don't understand is how to get python to make a windowed (GUI) application as opposed to a terminal based application. VB has drag and drop buttons, text boxes and so forth. What do i need to study in Linunx programming that lets me add a GUI to my programs.

zornan

---

### Post by Wybiral on 2007-01-02
Ouch... This is going to be difficult, but VB is a bad language to start with. Sure, it's easy and convenient, but it kindof distorts your perception of programming. Anyway, if you want a graphical gui editor, try glade. You can find it with your synaptic package manager. Good luck, python is a nice language.

---

### Post by zornan on 2007-01-02
yeah i learned that the hard way. my programs would only run on my computer. well they would run on other computers but not without installing runtime files, .net framework stuff. nothing but a pain in the rear. so yeah i want to do things right this time

---

### Post by pmasiar on 2007-01-02
IMHO [wxPython]("http://en.wikipedia.org/wiki/WxPython") is a good start

---

### Post by malcolmb on 2007-01-02
I knew how to program more generally before, then at school we had to take a course on VB.NET, and that is a real bad language for learning programming.

I tried out afterwards programming some gui apps with python and PyGTK, and thanks to the tutorials that were out there I had a good time with it.

Make sure to visit [http://learningpython.com/](http://learningpython.com/) the guy has great tutorials on all aspects of python programming.

---

### Post by Mirrorball on 2007-01-03
If you want to design graphical interfaces by dragging and dropping buttons, install Qt Designer. There is a script that converts the interfaces you make with Qt Designer into Python (PyQt) code, it comes with PyQt and is called pyuic.

---

### Post by ZuLuuuuuu on 2007-01-03
> **zornan said:**
> yeah i learned that the hard way. my programs would only run on my computer. well they would run on other computers but not without installing runtime files, .net framework stuff. nothing but a pain in the rear. so yeah i want to do things right this time

You should be aware that if you use Python, want to code GUI applications and distribute them, then you will have to ask your clients to have: Python, GTK (or wxWidgets) and PyGTK (or wxPython or Tk) and they should all appropriate versions. I think this is more painful than asking for dlls and .net framework. That's why, I suggest C, C++ or another compiled language, they are harder to learn but the results are better for what you want to do.

---

### Post by pmasiar on 2007-01-03
> **ZuLuuuuuu said:**
> You should be aware that if you use Python, want to code GUI applications and distribute them, then you will have to ask your clients to have: Python, GTK (or wxWidgets) and PyGTK (or wxPython or Tk) and they should all appropriate versions. I think this is more painful than asking for dlls and .net framework. That's why, I suggest C, C++ or another compiled language, they are harder to learn but the results are better for what you want to do.

I never needed it myself, but there are couple of python compilers which will create executable, linked with libraries IIUC. Another option, not as pretty but usable and with smaller footprint, could by curses-based interface. IMHO, YMMV.

---

### Post by Mirrorball on 2007-01-03
> **ZuLuuuuuu said:**
> You should be aware that if you use Python, want to code GUI applications and distribute them, then you will have to ask your clients to have: Python, GTK (or wxWidgets) and PyGTK (or wxPython or Tk) and they should all appropriate versions. I think this is more painful than asking for dlls and .net framework. That's why, I suggest C, C++ or another compiled language, they are harder to learn but the results are better for what you want to do.
Dependencies are not a problem with most Linux distributions, they are solved automatically when the program is installed. And even with C and C++, the shared libraries would still be needed.

---

### Post by ZuLuuuuuu on 2007-01-03
I forget to say that I also think about Windows. Like you say dependencies are not a problem for most distributions but if he also wants his program to be cross-platform, then installing the dependencies are pretty hard for an amateur Windows user, you should prepare a guide for an amateur client which dependencies are needed and where to download them. These seem to be easy for us but a user who faces the words "Python", "wxWidget", "wxPython" first, it is pretty hard :) From that point of view compiled languages have great advantage.

---

### Post by Mirrorball on 2007-01-03
OK, in this case, as pmasiar said, there is a program (called py2exe IIRC) that creates an executable file from a Python script and also includes all dlls.

---

### Post by TheIdiotThatIsMe on 2007-01-03
I'm afraid I'm not a programmer, and the only course I ever took was in VB also. For Linux, I used Realbasic for a while, which is very similar, and also cross platform. I wish you the best in luck on your programming adventures :)

---

