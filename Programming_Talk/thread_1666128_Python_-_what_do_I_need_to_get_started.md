---
title: "Python - what do I need to get started?"
date: 2011-01-13
forum: Programming Talk
---

### Post by Loki*PI on 2011-01-13
HI All - total newbie here. I want to teach myself python or at least make a run at it.  I've looked through the FAQ, gone to python.org, read several threads, etc, but still have the basic question, what do I need to get started with Python?  I've installed v3.1.  What else do I need? Software center has about 1250 items under python. 

Any helpful suggestions will be appreciated.

Thanks All

---

### Post by NightwishFan on 2011-01-13
Here are some helpful links to the rescue! :)

Google Python Lessons (i fixed link) [http://tinyurl.com/22kjx65](http://tinyurl.com/22kjx65)

[https://help.ubuntu.com/community/Programming/Python](https://help.ubuntu.com/community/Programming/Python)

This was the biggest help:
[http://www.tuxradar.com/content/python-pygtk-webkit-20-minutes](http://www.tuxradar.com/content/python-pygtk-webkit-20-minutes)

---

### Post by Loki*PI on 2011-01-13
Cool.  thank you very much I'll check them out.

---

### Post by Nytram on 2011-01-13
I started off learning Python with this tutorial:

[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6")

I'd recommend using Geany for writing your programs.

---

### Post by oldfred on 2011-01-13
I like the simple editor geany. You set it up to use spaces in place of tabs and save a file as .py and you can immediately run it and it will either work or show the errors. I find code on line, and can just copy, paste into a new page, save & run to find out how it works.

Editors:
Too many choices but many are free so you can try them
[http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors)

---

### Post by nvteighen on 2011-01-13
I want to warn you about something.

You've installed Python 3.1. Ok, perfect, that's the latest release. The problem is that that version still lacks third-party modules that are essential to do anything outside little code snippets. Nowadays, the "practical" Python versions are 2.6 and 2.7.

The situation is confusing and there's even a whole thread going on now discussing it in these forums ([http://ubuntuforums.org/showthread.php?t=1665207](http://ubuntuforums.org/showthread.php?t=1665207)). I'm not suggesting you don't learn Python 3.1, but that you should take this in account if you happen to plan a "real" project in the future that needs, say, a GUI or some math library.

---

### Post by nvteighen on 2011-01-13
I want to warn you about something.

You've installed Python 3.1. Ok, perfect, that's the latest release. The problem is that that version still lacks third-party modules that are essential to do anything outside little code snippets. Nowadays, the "practical" Python versions are 2.6 and 2.7.

The situation is confusing and there's even a whole thread going on now discussing it in these forums ([http://ubuntuforums.org/showthread.php?t=1665207](http://ubuntuforums.org/showthread.php?t=1665207)). I'm not suggesting you don't learn Python 3.1, but that you should take this in account if you happen to plan a "real" project in the future that needs, say, a GUI or some math library.

---

### Post by nvteighen on 2011-01-13
I want to warn you about something.

You've installed Python 3.1. Ok, perfect, that's the latest release. The problem is that that version still lacks third-party modules that are essential to do anything outside little code snippets. Nowadays, the "practical" Python versions are 2.6 and 2.7.

The situation is confusing and there's even a whole thread going on now discussing it in these forums ([http://ubuntuforums.org/showthread.php?t=1665207](http://ubuntuforums.org/showthread.php?t=1665207)). I'm not suggesting you don't learn Python 3.1, but that you should take this in account if you happen to plan a "real" project in the future that needs, say, a GUI or some math library.

---

### Post by Loki*PI on 2011-01-13
As I don't have a clue and Python 2.6.5 is default I was wondering if I should uninstall the 3.1 or at least just work with 2.6?  I came across other references that there was a big gap between 2.6 and the new 3.1 and 3.1 wasn't support extensively.  I'm think to stick to 2.6 and if it ever becomes an issue I can then jump to 3.1.  That a good strategy you think?

---

### Post by memilanuk on 2011-01-14
Not 'good' as in 'optimal' but its about the only one you have in reality.

---

### Post by Cheesehead on 2011-01-14
Depends what you want to do.
You can still do a lot in 3.x. And I think the gap is greatly overstated.

Pick a project. If the 3.x tools you need are available, then use it. If the 2.x tools haven't been upgraded yet, then use 2.x.

There is a great deal of grumbling and complaining thrown around during this transition from 2.x to 3.x. That's normal. And the transition is long - it will take a few more years. But the transition to 3.x *is* happening.

If you really want to learn how to use Linux, you'll be learning 2.x, 3.x, bash, and complex applications that are-not-actually-languages but necessary like dbus and gconf, and much more. Different projects are sometimes easier in different environments. For example, parsing the content of a web page for specific content takes about seven lines of very cryptic python, but only two simple lines of bash script.

---

### Post by Loki*PI on 2011-01-14
Long learning curve ahead.  Thank you all for the help.

---

### Post by Charlietech on 2011-01-15
I want to make some GUI's and was wondering if I should use 3.1 or 2.7.

---

### Post by Nytram on 2011-01-15
Not sure about the other toolkits but PyGTK hasn't been ported to Python 3 yet.

---

### Post by llanitedave on 2011-01-15
> **Loki*PI said:**
> As I don't have a clue and Python 2.6.5 is default I was wondering if I should uninstall the 3.1 or at least just work with 2.6?  I came across other references that there was a big gap between 2.6 and the new 3.1 and 3.1 wasn't support extensively.  I'm think to stick to 2.6 and if it ever becomes an issue I can then jump to 3.1.  That a good strategy you think?

There's no need to uninstall 3.1.  It's easy to have both versions installed, and simply choose which one when you call the interpreter:

```
yourpath:~$ python3.1

OR

yourpath:~$ python2.6

```

As a perennial python beginner myself, it makes sense to me to use 3.1 as your learning version.  Much of the syntax for 3.1 has been backported to python 2.6 and 2.7 anyway -- and the 2.xx lineage won't be upgraded any longer.

So if you need to do something in 2.6 or 2.7, you can still use most of what you've learned, and you don't have to maintain two different ways of doing things.

From what little comparing I've done, it appears that 3.1 has slightly better performance than 2.6.  I haven't compared it against 2.7.

---

