---
title: "Ubuntu minimal, evince, could not open x display"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by Qesty on 2013-09-25
I've installed minimal version of Ubuntu without GUI on local machine. I would like to open PDF file with evince. I've installed evince and xorg. 

evince file.pdf

Gives:

** (evince: 15309): WARNING **: Could not open X display

what can be a problem, and where can I get more info concerning running graphical apps in minimal version.

---

### Post by 7182818 on 2013-09-25
Have you started the X server yet?  Try running 'startx' to kickoff the server and get into the GUI, or, according to the man page, it looks like you could try 'startx evince file.pdf' to run evince and then exit when finished.

---

### Post by DuckHook on 2013-09-25
I like running minimal install on my servers which means that X or any DE for that matter is not installed. However, this means that you cannot use Evince to look at PDFs because Evince is a graphical app. In fact, with minimal install, you cannot use *any* graphical X-based app, so you must be sure that you are committed to the pure CLI interface if you want to run minimal install.

There are some frame buffer tools that will allow you to view graphics (like PDF files) on a CLI. However, they are generally considered hacker/geek tools and not "intuitive" like the familiar GUI interfaces and their friendlier Desktop Environments. Are you sure you are prepared to run without a DE? If so, then I use *fbgs* which has a number of dependencies the most important of which is *ghostscript* but all of which should be pulled down when you install *fbgs*.

**WARNING** The pure CLI environment is fascinating for those of us who treat Linux as a hobby and want to learn its inner secrets. However, it is overwhelming, intimidating and impractical for new users, who almost always need the familiarity of the GUI. If you are intent on running a minimal install, be aware of all that you are getting into.

---

### Post by verymadpip on 2013-09-26
Hi there.
I think you may need to install xinit to be able to start the x server.

---

### Post by Qesty on 2013-09-26
thanks a lot 2 all,

The problem was that I have not started X server: startx

DuckHook, I tried fbgs as well, but for some reason it widens the picture I want to view for the entire width of the console

---

### Post by DuckHook on 2013-09-27
When you mentioned "minimal install", I jumped to the conclusion that you did not even have X installed, and therefore, no desktop environment either. It did not occur to me that by having Evince even present in your system, you would already had to have installed X, a DE and all its attendant apps. My bad.

Since you are already running a DE and not a pristine minimal install, *fbgs* makes no sense. This is a frame buffer pdf reader for command line purists who forswear GUIs altogether and do not even have X installed. It is not relevent in your case and you don't need to bother with it any further.

---

