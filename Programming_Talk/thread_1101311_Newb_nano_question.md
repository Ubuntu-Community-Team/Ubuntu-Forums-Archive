---
title: "Newb nano question"
date: 2009-03-20
forum: Programming Talk
---

### Post by Shmook on 2009-03-20
What language is the default in nano?

I'm trying to show myself around python, and am checking out a tutorial -- it said any editor would work and I figured for now I'd keep it simple and use nano. I've encountered an error that I think is really simple -- that nano doesn't use python. Is this right?

And if I'm checking out python what editor should I use; or do you just use the in-terminal program that starts after the "python" command. Thanks

---

### Post by Anthon on 2009-03-20
I am not sure if nano uses python or if you can start python from nano on the currect editing buffer (like emacs can).

The in-terminal program is the python interpreter and has only limited editing facilities.

If you want to edit a file with nano I suggest you save it e.g. as abc.py on your desktop, then open a terminal (you can leave nano open) and run
   python ~/Deskstop/abc.py
to test the program.

---

### Post by aeiah on 2009-03-20
i program my python bits and pieces in [scite]("http://www.scintilla.org/SciTE.html"). its no better than old school solutions like vim or emacs or newer text editors, but it is available for linux and windows so i can have a familiar text editor at work and at home. hitting F5 runs the script in a frame at the side or bottom. has text highlighting for python, bash, java, html etc

---

### Post by Tek-E on 2009-03-20
> **Shmook said:**
> What language is the default in nano?

I'm trying to show myself around python, and am checking out a tutorial -- it said any editor would work and I figured for now I'd keep it simple and use nano. I've encountered an error that I think is really simple -- that nano doesn't use python. Is this right?

And if I'm checking out python what editor should I use; or do you just use the in-terminal program that starts after the "python" command. Thanks

Sadly you cant execute a python script inside nano.

---

### Post by abhilashm86 on 2009-03-20
> **Shmook said:**
> What language is the default in nano?

And if I'm checking out python what editor should I use; or do you just use the in-terminal program that starts after the "python" command. Thanks

if u want to program python, big programs have indentation stuff and hard to handle, so use [eclipse]("http://www.eclipse.org/"). After installing eclipse then follow guide to install pydev. So you can easily program in pyhton.

---

### Post by wmcbrine on 2009-03-20
I'm not sure I understand the question. Default language? Um... English? :D

I use nano to write Python programs, but I just do it like this:

nano file.py
[edit; save; exit]
python file.py

If nano has the ability to launch a Python interpreter directly -- or any other language's interpreter or compiler -- I am unaware of it.

And yes, use the interactive interpreter when you want to play around or test some ideas. But you can't edit or save anything from there.

---

### Post by Shmook on 2009-03-21
> **wmcbrine said:**
> I'm not sure I understand the question. Default language? Um... English? :D

Heh, right I think I get it now -- any editor can be used, since your just putting in code -- the only difference is what you save it as or what program you use to run it?

I was under the assumption that some editors only understand or recognize a certain language -- or automatically saved a file to be run using C.

Like I said -- newb here

So eclipse and scite, eh? I'll check those out. I do look forward to learning to use vim better but one step at a time. Thanks!

---

### Post by Shmook on 2009-03-21
Ah! so I see both eclipse and scint are IDEs. Is this what I should look for...basically, for now, I want to understand code and programming better so will just be going through tutorials and such.

And, so, to be clear, nano is strictly a text editor, not an IDE.

Shoulda posted this in AbsoluteBeginners forum I know...

---

