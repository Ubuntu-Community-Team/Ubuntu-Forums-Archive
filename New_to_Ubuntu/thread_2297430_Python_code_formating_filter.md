---
title: "Python code formating filter"
date: 2015-10-03
forum: New to Ubuntu
---

### Post by gam01hr on 2015-10-03
Dear forum,
I'm playing with python. I'm looking for some tool like "astyle" but for python code formating. I love "astyle" but it seems it doesn't work well for python code.
Astyle=Source code indenter, formatter, and beautifier for C, C++, C# and Java
Pls. advice.
Martin
Oops. solved with google:[https://pypi.python.org/pypi/autopep8](https://pypi.python.org/pypi/autopep8)

---

### Post by mystics on 2015-10-03
So you want something to fix your indentation? 

I don't personally use programs like this (more on this later), but here are a couple StackOverflow threads on the issue:
[http://stackoverflow.com/questions/1024435/howto-fix-python-indentation](http://stackoverflow.com/questions/1024435/howto-fix-python-indentation)
[http://stackoverflow.com/questions/2625294/how-do-i-autoformat-some-python-code-to-be-correctly-formatted](http://stackoverflow.com/questions/2625294/how-do-i-autoformat-some-python-code-to-be-correctly-formatted)

My advise for the future, though, is to get a good text editor that handles this for you, and you won't need to rely on external scripts to fix formatting errors. You've probably figured it out by now, but indentation is important to Python, and a good text editor will help tremendously with getting the proper formatting.

Microsoft's Visual Studio Code handles all of this very well. It auto-indents code and can also be set to replace tabs with four spaces, which is the standard format for Python.

If you have an aversion to Microsoft or want to stick to open source, Gedit has a plugin for this, but I've found Gedit and the plugin to still be overall inferior to Code. Either way, here it is: [https://code.google.com/p/gedit-intelligent-text-completion/](https://code.google.com/p/gedit-intelligent-text-completion/)

A couple other good text editors are Sublime Text and Atom, but in the case of the latter, I've often found it to mess up the tab settings, which can create problems when someone else uses a text editor that respects Python standards. So as much as I love Atom, it isn't a good Python editor. On the flip side, I know a lot of people who swear by Sublime, and a lot of them are Python programmers. 

Also, I haven't used it, but I'd imagine IDLE will handle all of this, given that it is the official Python text editor.

---

### Post by GreatDanton on 2015-10-04
I found PyCharm Community Edition the best editor for python code.

Vim handles indentation pretty well too, but it takes time to get used to it, so I would go with PyCharm.

---

