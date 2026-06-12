---
title: "Python..."
date: 2008-07-28
forum: Programming Talk
---

### Post by Warpster Buntu on 2008-07-28
Alright, I just started using Python yesterday.

I am using this tut:[http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)

I have finished the first two articles of the basic section, and I am getting somewhat confused. As most of you know, Python comes installed with 8.04, via a terminal command. But now that I am nearing the point of actually creating things, I'd like to know how I can save, and access some of the neat Python stuff, such as IDLE, because the way the tut describes it makes it sounds like the writer is using the actual program, with its own window, instead of turning the 8.04 terminal into Python.

Sorry if I am confusing anybody:)

---

### Post by tamoneya on 2008-07-28
in terminal run:```
sudo apt-get update
sudo apt-get install idle-python2.5
```
Then look in applications -> programming

[http://www.python.org/idle/doc/idlemain.html](http://www.python.org/idle/doc/idlemain.html)

---

### Post by Warpster Buntu on 2008-07-28
Cool, thanks!

So,this is basically the real version, right?

---

### Post by lukjad on 2008-07-28
Umm... as opposed to the unreal version? ;)
As far as I know, Python is an open source programming language. SO  that should be the real one. From the website:
> [Python is distributed under an OSI-approved open source license that makes it free to use, even for commercial products.]("http://www.python.org/")

---

### Post by Warpster Buntu on 2008-07-28
What I meant by real was not just a transformed Ubuntu terminal.

Anyway, thanks for the help everybody =)

---

### Post by imdano on 2008-07-28
I think you're misunderstanding what Python is.  When you run python in the terminal, you're getting the interactive python prompt, which is just a way of interacting with the language.  You can save any file with python code in it and then execute the code by running this in the terminal```
python <file name>
```If you add this to the first line of the file ```
#!/usr/bin/python
<rest of your code here>
```Then you can execute it like any other program (./filename).

IDLE is just a Python IDE.  It's basically a text editor specially designed for writing python code.  But you could also just use gedit or vim or emacs or whatever.

---

### Post by jimi_hendrix on 2008-07-28
> **imdano said:**
> IDLE is just a Python IDE.  It's basically a text editor specially designed for writing python code.  But you could also just use gedit or vim or emacs or whatever.

you can even use a C++ IDE but you would have to save it .py instead of .cpp and compile it elsewhere

---

### Post by tamoneya on 2008-07-28
> **Warpster Buntu said:**
> What I meant by real was not just a transformed Ubuntu terminal.

Anyway, thanks for the help everybody =)

I actually just use gedit.

---

### Post by LaRoza on 2008-07-28
See the sticky one how to make Python scripts and execute them. See the sticky on editors available as well.

---

### Post by Ed J on 2008-07-28
> **LaRoza said:**
> See the sticky one how to make Python scripts and execute them. See the sticky on editors available as well.

Not a bad idea but, where's the sticky?

---

### Post by LaRoza on 2008-07-28
> **Ed J said:**
> Not a bad idea but, where's the sticky?

On the index of this sub forum, at the top with the bold word "Sticky" next to it ;)

There is only one in this forum, and it links to other threads.

---

### Post by pmasiar on 2008-07-29
> **Warpster Buntu said:**
> What I meant by real was not just a transformed Ubuntu terminal.

When you open terminal window, one of Linux shells (most likely bash) interprets your input. When you start python (without program name), Python shell will take over. Interactive Python shell is one of the major cool features of the language, allowing beginner to explore language one line at a time, instead of forcing learner to write, compile and run small (but multiline) programs to explore each new feature.

See wiki in my sig for links how to learn Python.

---

### Post by Sinkingships7 on 2008-07-29
Geany will edit python (.py) files and run them by simply saving and pressing F5.
```
sudo aptitude install geany
```

---

