---
title: "Eclipse - PyDev can't seem to get it to work"
date: 2007-05-03
forum: Programming Talk
---

### Post by gotquestions on 2007-05-03
I installed Eclipse, then PyDev. On Eclipse: Windows> Pref > PyDev > Interpreter Python
I put on Python interpreter:
/usr/bin/python
/usr/bin/python2.4
...later on it ask me if i want to add all those system libs. I said yes and it added a chunk of stuff to the System PYTHON PATH and Forced builtin libs.

So now I am back on the main page. I select: File > New > PyDevProject
I enter Project name. it says chose project type: I chose python 2.4 even thogh i have 2.3, 2.5
there is a checkbox that is checked. Create default 'src' folder and add it to the python path?

I click finished and I get this:
a popup box:
IDEWorkBenchMessages.CreateProjectWizard_errorTitle

-Error storing pydev project descriptor:P/hello

So what am I doing wrong?

I am a beginner

---

### Post by skeeterbug on 2007-05-03
> **gotquestions said:**
> I installed Eclipse, then PyDev. On Eclipse: Windows> Pref > PyDev > Interpreter Python
I put on Python interpreter:
/usr/bin/python
/usr/bin/python2.4
...later on it ask me if i want to add all those system libs. I said yes and it added a chunk of stuff to the System PYTHON PATH and Forced builtin libs.

So now I am back on the main page. I select: File > New > PyDevProject
I enter Project name. it says chose project type: I chose python 2.4 even thogh i have 2.3, 2.5
there is a checkbox that is checked. Create default 'src' folder and add it to the python path?

I click finished and I get this:
a popup box:
IDEWorkBenchMessages.CreateProjectWizard_errorTitle

-Error storing pydev project descriptor:P/hello

So what am I doing wrong?

I am a beginner

For your interpreter you put a path to python2.4, when you said you had 2.3/2.5 installed. Try doing:

$> python -V
$> whereis python

This should tell you what version you are using and where the executable is located. I only have PyDev installed on my Windows XP box so my interpreter path in PyDev is C:\python24\python.exe

---

### Post by gotquestions on 2007-05-04
doesnt work.

cloud@cloud-desktop:~$ python -V
Python 2.4.3
cloud@cloud-desktop:~$ whereis python
python: /usr/bin/python /usr/bin/python2.4 /etc/python2.4 /usr/lib/python2.3 /us r/lib/python2.4 /usr/bin/X11/python /usr/bin/X11/python2.4 /usr/local/lib/python 2.4 /usr/include/python2.4 /usr/share/man/man1/python.1.gz

---

### Post by gotquestions on 2007-05-04
help? i believe my interpreter is correct

---

### Post by bendowling on 2007-06-11
> **gotquestions said:**
> help? i believe my interpreter is correct
What is the output of ls -l /usr/bin/python

---

### Post by pmasiar on 2007-06-11
> **gotquestions said:**
> 
So what am I doing wrong?

I am a beginner

Are you required to use eclipse/pydev? maybe you want to try much simpler Python IDE, like IDLE or SPE - both are installed by synaptic without a glitch?

---

