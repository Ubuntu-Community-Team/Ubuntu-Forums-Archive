---
title: "simple IDE/editor w/ GOOD python code completion"
date: 2012-05-02
forum: Programming Talk
---

### Post by memilanuk on 2012-05-02
...yes, I know.  Another Python IDE thread ;)

This time with a slightly different twist:  *[COLOR="Blue"]I'm looking for something that does intelligent code completion based on the modules being imported in the script I'm writing[/COLOR]*.  Specifically with PyQt4...

PyScripter seems to (for the most part) do what I'm looking for, without being too over-the-top.  Unfortunately, being written in Delphi for the M$ Windows platform, it ain't gonna be ported to Linux anytime soon.  Some people have gotten it working via WINE, but so far its being a little bit obstinate for me.

Komodo Edit kinda does it... Geany & Gedit do not... Eric4 seems b0rked in 12.04 (only installs in spanish on my U.S./American/English OS install)... Spyder seems to do it, but I'm still pretty much feeling my way around it.  I'd really rather not have to pay for Wing IDE Personal or PyCharm if I don't have to...

TIA,

Monte

---

### Post by MG&amp;TL on 2012-05-02
I quite like DreamPie + Geany. Usually, I split the screen into the two windows. Makes Gtk &co much easier if noting else.

---

### Post by memilanuk on 2012-05-10
So... been playing more with Spyder, and setting up (again) Eclipse/PyDev (had to re-install for unrelated reasons).  Both seem to do pretty good code completion; enough so that it makes it a *lot* easier figuring things out with a gui toolkit (PyQt4).  Still not sure how much I like the need to set up 'project' folders with sub-directory structures for what are still fairly simple scripts of one to maybe three modules.  

Anywho... kind of going off on a tangent here... any real preference between Eclipse (from the repos) with PyDev installed vs. Aptana Studio 3 which comes with some things besides just PyDev built in, but requires a non-standard - for Ubuntu - Java JDK to be installed.  Anticipated primary use is going to be Python 2.x/3.x + desktop GUI stuff like pyqt4, pyside, tkinter, wxpython... and maybe some cherrypy/web2py web framework with html/css/js on the side (eventually).

TIA,

Monte

---

### Post by Carpentr on 2012-05-10
I use Wing IDE Personal from time to time. I know you are hesitant, but I've always thought it was a good investment. It is priced decently as well.

If you're working on an open-source project they'll supply you with the IDE for free, also.

---

### Post by 3Miro on 2012-05-10
I use Geany for my Python needs. I am not sure what your definition of "good code completion", but I find Geany's to be exactly what I need. You may not like that it is broad, i.e. it doesn't parse to code to distinguish which function belongs to which class, it simply lists all functions and variables that complete the typed characters. This behavior is good enough for me and IMO it is offset by Geany's fast speed.

---

### Post by memilanuk on 2012-05-11
Unless there is some trick to code completion in Geany that I haven't discovered yet, its very limited compared to what is present in Eclipse + PyDev.  I thought I had it figured out in Spyder, but I may not have things configured right on this new (re)install yet.

In Geany:

class MyForm(Qt <Ctrl+Space> gets me a dropdown list of QtCore, QtGui.  The next part would be QDialog, as in 'Class MyForm(QtGui.QDialog):'.  Typing QD <Ctrl+Space> gives me nothing.

In Eclipse + PyDev... just typing class MyForm(Qt starts the autocompletion, as it displays all the various possibilities.  As I keep typing, it keeps narrowing the list, including once I type the '.' and start QD...  The difference is just so marked it has to be seen to be believed, I think.

Both Spyder and PyDev have some form of built in code-checking...  another one of those things that I didn't think much about until I saw it in action.  Having the editor actively flagging your code with errors (failed imports) or warnings (unused imports) according to the 'approved' Python style guides can be very helpful... although I'll admit the warnings about 'from foo import *' can occasionally be annoying - and easily enough ignored ;)

I think I'm finally starting to see the benefit of a good IDE, even if I don't even come close to needing/using half of the proverbial kitchen sink they provide... though editors like Geany and Gedit will probably always have a place on my computers for simpler stuff.

---

