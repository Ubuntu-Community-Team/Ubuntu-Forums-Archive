---
title: "Change my BASH scripts into a GUI"
date: 2008-08-25
forum: Programming Talk
---

### Post by anotherdisciple on 2008-08-25
Hey all,

        I have this awesome little bash script that I wrote a while back. I wrote it for two reasons. First, for myself... I do a fresh install of each version of ubuntu, so this sets up things the way I like them in 1/4 the time. Second, for the few people who I have talked into trying linux. It asks them questions and installs things for them... that way they don't have to go searching the forums for common things like installing ccsm or avant-window-navigator. It does a lot of stuff and asks a lot of questions.

         I wanted to take it one step further. Most of these new users are intimidated when I tell them to save the file to their home folder, open the terminal, and type sudo ~/nubuntu (the name of my script. then to watch a terminal screen and wait for questions. I would much rather make a GUI. That way all they have to do is click on an icon, a window pops up, and they click yes or no to every question.

So the question is. Is there a way that I can use my bash script to make a GUI, or should I just learn how to use python and convert all the ideas over? I've been meaning to learn Python anyways, but I am having trouble finding a simple yet very detailed tutorial on this. I have heard of Zenity, but haven't had the chance to look it up yet.

Let me know what you think is the best route.

---

### Post by raul_ on 2008-08-25
Being a programmer myself, I would say to port the code. It's a good excuse to start learning Python anyway. Check out LaRoza's tutorials for Python.

---

### Post by sdennie on 2008-08-25
I would use zenity.  I think it will probably do exactly what you want.  Have a look at the man page:

```

man zenity

```

---

### Post by phidia on 2008-08-25
Google is your friend again. [Here]("http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2008-07/msg00128.html") is a page on what you asked, and for a good python beginners guide + many other programming links check out [this]("http://ubuntuforums.org/showthread.php?t=832449").

---

### Post by raul_ on 2008-08-25
> **vor said:**
> I would use zenity.  I think it will probably do exactly what you want.  Have a look at the man page:

```

man zenity

```

But you would still have to run it from the terminal right?

---

### Post by anotherdisciple on 2008-08-25
> **raul_ said:**
> But you would still have to run it from the terminal right?

I'm thinking yes... hmmm... maybe python is the way to go. Can I get python to do things that require root access?... Like installing a program, etc?

How long would you guess it would take to learn how to write a simple GUI... one that just pops up some plain gray windows and asks yes or no questions? It would just install, change config files, etc based on the user input.

---

### Post by mssever on 2008-08-25
> **anotherdisciple said:**
> I'm thinking yes... hmmm... maybe python is the way to go. Can I get python to do things that require root access?... Like installing a program, etc?

How long would you guess it would take to learn how to write a simple GUI... one that just pops up some plain gray windows and asks yes or no questions? It would just install, change config files, etc based on the user input.
Running it from the terminal is a separate issue from the language you write it in.  If you make a GUI, you'll need to either include a shebang line and have users set execute permissions before double-clicking it, or possibly make a deb file which includes a .desktop file in /usr/share/applications that will add a menu item.

---

### Post by jpeddicord on 2008-08-25
Moved to Programming Talk.

---

### Post by themusicwave on 2008-08-25
Depending on how your scripts are written, I would just make a GUI that simply calls the scripts and sends the appropriate input.

The big advantage of this is then you have the choice of using the GUI or using the CLI.

This of course assumes that the scripts take command line inputs.  

What I would do is make the user interface build a string of command line arguments based on the items selected.  Once done picking things the user clicks a button like "configure" and it calls your script in the background, passing all the arguments and then waits for it to finish.

It's your call though.

---

### Post by y-lee on 2008-08-25
> **anotherdisciple said:**
> I'm thinking yes... hmmm... maybe python is the way to go. Can I get python to do things that require root access?... Like installing a program, etc?

How long would you guess it would take to learn how to write a simple GUI... 

Yes python is a real programming language and can do basically anything any other language can. As to how long it would take to learn to write a GUI in python that would depend upon your previous programming experience. I started to learn python a month ago and within a week had a more or less complete GUI application, using wxPython.

But i have programmed before in other languages so how long for you is going to depend upon your current level of knowledge and skill.

I believe vor recommended zenity, zenity is a good choice for a simple GUI like bash application. it should only take a brief look at the man page to get that going. lol.

---

