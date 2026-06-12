---
title: "Some Python questions"
date: 2006-02-18
forum: Programming Talk
---

### Post by Xecuter on 2006-02-18
Hi! I've been using Python for allmost to years now on Windows.
But I've got 2 questions:

1. I've newly gotten Linux and I find programming better there. But is there any way to get the Python IDLE that comes with the Windows edition in Linux? I now it's possible to use gedit, and there's a integrated interpreter in the terminal. The one that I'm looking for is the one that comes in a window, and where you can press File -> New and get a text editing kind of window up (instead og gedit). I liked this because there were automated space handling and colors and so on. You could also press F5 and the code will run.

2. I've the only one doing programming and using Linux in my friend sircel, so I have to convert .py to .exe. Will GUI I've made with GTK come in the .exe package when I've used py2exe, or do they have to install GTK or something to make it work?

---

### Post by gord on 2006-02-18
idle is in the repositorys, to a search for idle in synaptic and you'll find it there (assuming youv enabled extra repositorys)

> 
2. I've the only one doing programming and using Linux in my friend sircel, so I have to convert .py to .exe. Will GUI I've made with GTK come in the .exe package when I've used py2exe, or do they have to install GTK or something to make it work?


im guessing that english isn't your first language and im finding this kinda hard to follow so if im off the mark don't blame me ;) 

if your using ubuntu gkt is allready installed for you and you don't have to convert your python files to .exe, just add "#!/usr/bin/env python" to the top of your .py file and you can run it like a regular program

if you are talking about having your gui python programs running on windows i would suggest looking into wxpython. allthough i beveleve you can get GTK for windows i wouldn't suggest it.

---

### Post by sapo on 2006-02-18
1 - just type this in the terminal:
```
sudo apt-get install idle
```

2 - I think that they will have to install the GTK stuff on windows to run the exe

---

### Post by Xecuter on 2006-02-18
[QUOTE=gord]im guessing that english isn't your first language and im finding this kinda hard to follow so if im off the mark don't blame me ;) 
[/QUOTE]

Yep! I'm from Norway :D
I had trouble formulating that sentence too, so I don't blame you ;). Let me try again:

I've made a GUI program with GTK. Then I want to convert the program into .exe so that it can run on Windows. For this I use py2exe, which I've only tried with console programs. Does the Windows box need to have GTK installed to run the program then? Or will py2exe take care of this?

I know there's a command in py2exe that makes GUI executables, which means there is no console in the background. I don't know if it means including GTK.

---

### Post by gord on 2006-02-18
yea if people want to use the program you'v created that uses gtk, they will also need to have gtk. 

and i beleve that when py2exe makes gui executionables it is just refering to the fact that it doesn't open a console and keeps all that stuff hidden.

---

### Post by Wallakoala on 2006-02-18
for your first question, you can just type:
```
sudo apt-get install idle
```
There is a much better ide out there called Stani's Python Editor, I would recommend checking that out also.

---

### Post by ow50 on 2006-02-18
[How can I bundle a PyGTK program in windows so my users don't need to install Python or the GTK+ libs?](http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq21.005.htp)

---

### Post by Xecuter on 2006-02-19
I noticed that SPE is written for i386 architecture. Will it work when I upgrade my kernel to k7?

---

### Post by Revert on 2006-02-19
[QUOTE=Xecuter]I noticed that SPE is written for i386 architecture. Will it work when I upgrade my kernel to k7?[/QUOTE]

Yes.  i386 is used a lot because it's older and all of the other, newer ones still support it (as I understand).

---

### Post by Xecuter on 2006-02-19
[QUOTE=Revert]Yes.  i386 is used a lot because it's older and all of the other, newer ones still support it (as I understand).[/QUOTE]

You mean its backwards compitable, right. I thought so, I just needed to be sure.

---

### Post by stani on 2006-02-20
[QUOTE=Xecuter]I noticed that SPE is written for i386 architecture. Will it work when I upgrade my kernel to k7?[/QUOTE]

In fact SPE is 100% pure Python so it is architecture independant. It depends on Python and wxPython. If these work, SPE will work as well.

---

