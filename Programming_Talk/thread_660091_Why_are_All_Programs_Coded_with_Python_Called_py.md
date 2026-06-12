---
title: "Why are All Programs Coded with Python Called *py*?"
date: 2008-01-06
forum: Programming Talk
---

### Post by Majorix on 2008-01-06
Yes, why do they have py in their name?

Are we forewarned that the program won't be like a program coded in another language? What the heck?

---

### Post by Auria on 2008-01-06
Why do all KDE programs begin with 'K'?
Why do many Gnome programs begin with 'G'?

etc. ;)

---

### Post by Majorix on 2008-01-06
That's a different story. They tell under which DE they are meant to work. Or work the best.

---

### Post by Wybiral on 2008-01-06
Because it's fun?

---

### Post by Majorix on 2008-01-06
Haha Wybiral your project's name also inspired me to create this topic :D

---

### Post by Jessehk on 2008-01-06
It's a naming convention.

Gedit, Gnome, gftp, etc
KWrite, Konqueror, Krita, etc
iMac, iTunes, iPod, etc

EDIT: That was **way** too fast. When I posted, there were no responses.

---

### Post by LaRoza on 2008-01-06
.py is expected by the interpreter usually when importing. Also .pyo and .pyc are used for compiled Python files which are also importable.

In Windows, .pyw is used for GUI programs.

It is not just a convention.

If you have a file called "functions.py", and you import it, you use the line "import functions". When it is imported, it is compiled and a new file named "function.pyo" is created. For future imports, the .pyo is imported not the original. If you alter the original and try to import it, it won't work, you have to reload it.

---

### Post by Wybiral on 2008-01-06
> **Majorix said:**
> Haha Wybiral your project's name also inspired me to create this topic :D

Well it's a library, not a program. I think this may be the case for most Python projects... They're usually written in a reusable module form, so it makes sense to declare it as a Py module (because other Python coders are welcome to use the module in Python). Mine gets its name from ECMAScript + Python.

---

### Post by Majorix on 2008-01-06
> **LaRoza said:**
> .py is expected by the interpreter usually when importing. Also .pyo and .pyc are used for compiled Python files which are also importable.

In Windows, .pyw is used for GUI programs.

It is not just a convention.

If you have a file called "functions.py", and you import it, you use the line "import functions". When it is imported, it is compiled and a new file named "function.pyo" is created. For future imports, the .pyo is imported not the original. If you alter the original and try to import it, it won't work, you have to reload it.

I didn't mean the extension. I meant the name. If you would go ahead and search for "py" in Synaptic you would be shocked at how many programs have it in their name.

---

### Post by LaRoza on 2008-01-06
> **Majorix said:**
> I didn't mean the extension. I meant the name. If you would go ahead and search for "py" in Synaptic you would be shocked at how many programs have it in their name.

oh, I see now.

I am not shocked, I saw them :)

---

### Post by rcsarver on 2008-01-06
what is the meaning of life?

---

### Post by LaRoza on 2008-01-06
> **rcsarver said:**
> what is the meaning of life?

42, but this is the programming talk forum, not the Cafe.

---

### Post by pmasiar on 2008-01-06
py in Python-based project names is insider joke, but not all Python-based projects have Py in names, IMHO minority does. Those with Py are just more visible.

You may also search google, it is common knowledge  that "all the good names are taken" :-)

There are many many Python projects without Py in name, ie:
- games: galcon, EVE online, 
- web frameworks: TurboGears, Django, Satchmo, tinyerp, 
- templating systems: kid, genshi ('papyrus' was considered, but was taken for some worthless eclipse project :-( )
(warning: shameless self-promoting plug)
Even my own project, visual game editor for kids, is called [GameBaker](http://code.google.com/p/game-baker/), no py in sight :-)

---

### Post by pmasiar on 2008-01-06
> **rcsarver said:**
> what is the meaning of life?

> **LaRoza said:**
> 42

This is common misunderstanding.

42 is not the meaning of life, but error code:

"42: no meaning of life found" :-)

---

### Post by Acglaphotis on 2008-01-06
Meaning of life, you say?
Cheese, of course.

---

### Post by jespdj on 2008-01-07
In my opinion, it is a bad idea to use the "py" prefix for your Python programs; certainly if the program is an end-user program (and not a library to be used by other developers).

The user doesn't care and doesn't need to know in which programming language a program is written. Non-programmers know nothing about Python, they probably even don't know that there is a programming language called Python. Those strange "pySomething" names will only confuse the end user.

Programs meant for end users should not have technical names.

---

### Post by engla on 2008-01-07
many nice packages for python have python in the name though, and I think of "foopy" as a name signalling "foo for python". For example numpy, sympy (numerical package for python, symbolic math for python). In this area I think the *py* use is motivated.

---

### Post by Wybiral on 2008-01-07
> **jespdj said:**
> In my opinion, it is a bad idea to use the "py" prefix for your Python programs; certainly if the program is an end-user program (and not a library to be used by other developers).

The user doesn't care and doesn't need to know in which programming language a program is written. Non-programmers know nothing about Python, they probably even don't know that there is a programming language called Python. Those strange "pySomething" names will only confuse the end user.

Programs meant for end users should not have technical names.

I actually can't think of any PROGRAMS that use the "*py*" convention, they are mostly libraries (in which case, it makes sense). But even if they are, and the user doesn't know wtf "*py*" means, how is it any different from "*"?

For instance, the default bit torrent client in Ubuntu, written in Python, but named "bitTorrent". I would absolutely understand if it used a library named "pyBitTorrent" (I don't know what it uses TBH). How many "*py*" PROGRAMS are there?

---

