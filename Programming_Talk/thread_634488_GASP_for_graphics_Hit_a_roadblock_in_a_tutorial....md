---
title: "GASP for graphics? Hit a roadblock in a tutorial..."
date: 2007-12-07
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-12-07
I'm using the Think Like a Computer Scientist tutorial and it's very, very good to fill in all those little holes I have as a programmer. However, Chapter 4 calls for GASP which I get an error when importing. Where can I get this, or how can I fix my problem?

The section: [http://www.ibiblio.org/obp/thinkCSpy/chap04.html#auto10](http://www.ibiblio.org/obp/thinkCSpy/chap04.html#auto10)

The error:

```

>>> from gasp import *
    Traceback (most recent call last):
      File "<pyshell#0>", line 1, in <module>
        from gasp import *
    ImportError: No module named gasp

```


What to do?

---

### Post by Wybiral on 2007-12-07
GASP isn't part of the standard Python modules (and it doesn't appear to be in the repositories). Try this: [https://launchpad.net/gasp](https://launchpad.net/gasp)

EDIT:

Apparently it was supported until Gutsy: [https://launchpad.net/ubuntu/gutsy/+source/python-gasp](https://launchpad.net/ubuntu/gutsy/+source/python-gasp)

---

### Post by ThinkBuntu on 2007-12-07
Not running Ubuntu, so no help. I located the zipped source (gotta love "it is available on our Download page" when there's no download page there!) from Launchpad, but now can't figure out how to load the thing. No useful documentation regarding installing this in sight...

---

### Post by Wybiral on 2007-12-07
You should be able to move the folder with the module into your project folder and import from there. Otherwise you have to move it to the appropriate Python path.

---

### Post by ThinkBuntu on 2007-12-07
[LIST]
[*]Downloaded archive, unpacked
[*]Renamed folder "gasp", moved to project folder
[*]Add 'from gasp import *' to new file, then begin_graphics()
[*]Still doesn't work
[*]Frustrated that such a tutorial wouldn't guide the reader on how to do this...
[/LIST]

---

### Post by Wybiral on 2007-12-07
OK, the folder inside the ".gz" package named "gasp" should work. Copy the gasp folder into your project directory (not the files from it, but the folder itself) and it should work.

EDIT:

Maybe that's the point of the lesson, lol, coping with crappy documentation :)

---

### Post by suminty on 2008-01-14
add this in ur source list and u ll get all python modules 

>deb [http://ppa.launchpad.net/mattva01/ubuntu](http://ppa.launchpad.net/mattva01/ubuntu) gutsy main restricted universe multiverse

---

### Post by twooften on 2008-02-05
[https://answers.launchpad.net/gasp/+faq/31](https://answers.launchpad.net/gasp/+faq/31)

Finally something straight forward...
I have been looking as well, for what seems like an eternity, but really only 2 days.

---

### Post by mlissner on 2008-12-09
Sigh. Now that link to launchpad is not working...onward I trudge.

---

### Post by mlissner on 2008-12-10
Ha! Found it: [http://dev.laptop.org/pub/gasp/downloads/](http://dev.laptop.org/pub/gasp/downloads/)

---

### Post by mlissner on 2008-12-16
Found something else today. If people are reading through the how to think like a computer scientist article, appendix A seems to be up to date with how to install GASP.

---

