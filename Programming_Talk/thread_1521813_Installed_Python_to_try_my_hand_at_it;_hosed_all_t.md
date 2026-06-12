---
title: "Installed Python to try my hand at it; hosed all the Python apps on my system."
date: 2010-07-01
forum: Programming Talk
---

### Post by snurfle on 2010-07-01
Sorry if this is a double post... I thought I posted it correctly, but it does not show up in my show all your posts" section...

Yes, I did read the FAQ...

I have been a VB programmer for years, a Linux user for 5 years, and have been dabbling in GAMBAS for about a year.
I decided to try my hand at Python the other day...
I downloaded 2.6.5 from python.org, and installed it on my machine (Lucid running on a Dell Inspiron B120, no dual boot, just a straight up Linux machine).
I played around with the tutorials on the python site; tried the "Hello World" app, a few math functions and some string functions. All seemed well.
I decided to play a sudoku before bed, and for some reason the program would not launch... just the spinning "waiting" cursor which would then disappear after about 10 seconds.
Hmmmm.
I rebooted my machine this morning after a kernel update, and now...

No desktop icons at all
I cannot launch nautilus either from menus or from the command line
Most of the apps in AWN are not working
Sudoku and Chess do not launch
I do not know what else is broken; but the AWN apps and the 2 games are written in python, which leads me to believe that installing Python on my system somehow hosed the applications which use Python...

I tried reinstalling sudoku just to see if that would help out... but it did not.

My system is essentially unusable at this point other than a few applications... (Chrome, for one!)...

Any idea how to proceed from here?

Thanks.

---

### Post by wmcbrine on 2010-07-01
I'm not sure exactly how to recover from your current situation, but for future reference, there was no need to download anything -- Python was already installed. Well, I guess you figured that out. But make a general principle of it: Before you go to a website and download a package, *look for it in the repos first*. Pull up Synaptic and do a search. You may find that it's already installed; if not, it's very likely that you can install it from there. Only if it's not in the repos (or, perhaps, if you really need a more recent version than is in the repos) should you consider installing it from a website.

Now as to your problem... I don't know what happens when you install from a package from python.org, but I'm guessing that it went in /usr/local/bin, and is overriding the system Python in /usr/bin. So the simplest thing might be to open a terminal and type "sudo rm /usr/local/bin/python". (Then restart.) It might also be possible to do a "make uninstall" in the directory where you installed it from.

If you can't start a terminal from the GUI, press Ctrl-Alt-F1 to get a text terminal.

P.S. The reason it breaks everything, even though it's a working installation of Python, is presumably that all the libraries (except the standard library) are installed only for the system Python -- so, for instance, PyGTK won't be found, making it impossible for many GUI apps to run.

---

### Post by StephenF on 2010-07-01
> **wmcbrine said:**
> So the simplest thing might be to open a terminal and type "sudo rm /usr/local/bin/python". (Then restart.)
I'd go after python2 and python2.6 as well but really I would just repeat the install process but do a make uninstall instead as that's the cleanest way.

---

### Post by wmcbrine on 2010-07-01
My worry is that it would be *too* clean, removing bits of the system Python as well. Probably baseless, but without knowing exactly what's in the makefile, I can't say. But, if you did go that route, then a reinstall of the system Python via a package manager afterwards might be enough to keep things in order. Or not... I can just imagine this ending up in a full reinstall of Ubuntu. :eek:

---

### Post by snurfle on 2010-07-02
I spent several hours yesterday unable to do anything on ubuntuforums... none of my posts showed up after I submitted them, not even in my "show all my threads" list; after trying to log out and back in, I spent over an hour trying to log in, but my password (and all forum-generated passwords as well) failed to work at all... I finally got disgusted with the whole mess and just walked away for a few hours.
I ultimately went onto the python irc channel and asked there and had a reply within 2 minutes...

> as root or via sudo run this command:
rm -rf /usr/local/lib/python2.6 /usr/local/include/python2.6 /usr/local/bin/python 

Then run hash -r and logout

in your shell you might run hash -r once too, but after that you'll all fixed up
copy and paste that rm command EXACTLY like it is or bad things could happen

Problem solved.  Everything is back to normal now, I can (finally) log back into ubuntu forums... apologies for posting the same thing multiple times.

> but for future reference, there was no need to download anything -- Python was already installed. Well, I guess you figured that out. But make a general principle of it: Before you go to a website and download a package, look for it in the repos first. Pull up Synaptic and do a search. You may find that it's already installed; if not, it's very likely that you can install it from there. Only if it's not in the repos (or, perhaps, if you really need a more recent version than is in the repos) should you consider installing it from a website.
Well... As far as the programming interface already being installed; I did not realize that at all.  I knew that Python is the language of choice for a LOT of applications on my system, I did not know that the developers platform was already installed.  (Biggest reason - no icon in the menu, plus a blue million hits for the word "Python" in the package manager!)  I know better than to go outside the package manager; 99% of the time everything is right there.  In this case, however, I guess 20/20 hindsight makes it obvious.

At any rate, I appreciate the assist.
Thank you.

---

### Post by wmcbrine on 2010-07-02
Python is an interpreted language; there's no separation between the development environment and the runtime environment. If you've got a Python app, you've got the interpreter. (Exception: A Windows app packaged with py2exe could have a cut-down version of the interpreter. But in most Linux systems, you'd just make the standard Python package a dependency, so it would be installed whenever a Pyhton app was.)

Not in the menu... yeah. You could probably get a menu entry by installing IDLE, but personally I don't like IDLE. Just open a terminal and type "python", and you've got an interactive session. But of course you can't save code from that -- use a text editor. That's about all the development environment I've used for Python, although I understand there's some support for it in IDEs like Eclipse.

---

