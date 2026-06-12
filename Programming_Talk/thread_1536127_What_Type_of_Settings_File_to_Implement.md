---
title: "What Type of Settings File to Implement?"
date: 2010-07-21
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-07-21
Hey guys, I am making an auto-archiver/backup sort of thing in Python([http://sourceforge.net/projects/frozendirectory/](http://sourceforge.net/projects/frozendirectory/)). As of now it uses an ordinary text file to store its small amount of settings(but ever growing). I was thinking of changing it to an XML file so that it would be more flexible/scalable and thus easier to work with in the long run. However, when I asked a friend he recommended that I just keep it in a python file, such as settings.py and just use 'import settings' from the file that needs the settings when needed. He claimed that it takes less space and I would only have to write code to write to the settings file as opposed to worrying about both reading and writing.

His points were convincing but made me wonder why no other large programs used the technique he is recommending.

So anyways, I just wanted to know what you guys think. Should I go with XML, .py, or something else? Thanks in advance.

---

### Post by jeffathehutt on 2010-07-21
Personally I prefer to use [ConfigParser]("http://docs.python.org/library/configparser.html") in Python.  That way, it is easy to use from your program, but also easy for users to edit it by hand if they want to (assuming you want the users to have that capability of course ;)).

---

### Post by Barrucadu on 2010-07-21
Ew, XML config files. Only go for XML if you're certain that nobody will ever want to eit it manually, as they are awful for that. Good for machines, terrible for people.

I'd personally just go for a plain "key = value" syntax, like most other config files. Though I have used the Python method for scripts before, which was quite nice.

---

### Post by nvteighen on 2010-07-22
There's another possibility, used for example on SuperTuxKart and obviously, Emacs: using Lisp code, which is essentially the same as XML but it could be executed right away without any further parsing if you embed a small Scheme interpreter (e.g. guile) or an ELisp one into your program.

---

