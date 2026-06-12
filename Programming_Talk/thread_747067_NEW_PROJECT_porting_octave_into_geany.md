---
title: "NEW PROJECT: porting octave into geany"
date: 2008-04-06
forum: Programming Talk
---

### Post by slimdog360 on 2008-04-06
I'm sick of it and I'm sure most of you are too. Getting a reasonable front-end to octave is something which we have wanted for ages, something simple and works well.

Well I'm going to port the octave language over into geany. We won't have an interface the like of Matlab, but it will let us run our octave programs as we would from the matlab text editor, with colour coding, syntax checking and the ability to run the program fly.

If anyone wants to help then post here. I've only just decided to do this so I havn't planned to much. I did have a look at the filetype files for geany and it doesn't look to hard to port over.

[Octave]("http://www.gnu.org/software/octave/")
[Geany]("http://geany.uvena.de/Main/HomePage")

---

### Post by lnostdal on 2008-04-06
have you seen texmacs? .. it's quite nice: [http://www.texmacs.org/tmweb/home/screenshots.en.html](http://www.texmacs.org/tmweb/home/screenshots.en.html)

i've used it connected up with Maxima, but it has support for Octave also (i haven't tried this though)

---

### Post by ad_267 on 2008-04-30
Wow I was just thinking about this. I was thinking about how a gtk front end for octave would be good last night and just now when I was using geany and using the terminal I thought that it would be great for use with octave. Just having syntax highlighting for octave/matlab in geany would be really helpful. I did a google search for "geany octave" and came up with this!

I will try and help out if I can but I don't have that much free time at the moment and my programming knowledge is pretty minimal.

Looks like this is what we need to know:
[http://geany.uvena.de/manual/dev/index.html#filetype-definition-files](http://geany.uvena.de/manual/dev/index.html#filetype-definition-files)

Also it may be useful to use the .lang file used by gedit as a reference. This is in  /usr/share/gtksourceview-2.0/language-specs/octave.lang
Also I've found the vim highlighting to be good so I've attached that too.

Ok after a bit more looking around it looks like it's not that easy to add a new file type, some changing of the source code will need to be done. See [http://geany.svn.sourceforge.net/viewvc/*checkout*/geany/trunk/HACKING](http://geany.svn.sourceforge.net/viewvc/*checkout*/geany/trunk/HACKING)

---

### Post by ad_267 on 2008-04-30
It looks like there is a LexMatlab.cxx file available for scintilla already so this shouldn't be too hard to get working with Geany.

Sourceforge seems to be down or just not working for me at the moment so I can't download the Scintilla source but I found LexMatlab.cxx here: [http://www.codase.com/search/display?file=L2dlbnRvbzIvdmFyL3RtcC9yZXBvcy9jb2Rhc2UuYy9zY2l0ZS0xLjYuMi93b3JrL3NjaW50aWxsYS9zcmMvTGV4TWF0bGFiLmN4eA==&lang=c%2B%2B](http://www.codase.com/search/display?file=L2dlbnRvbzIvdmFyL3RtcC9yZXBvcy9jb2Rhc2UuYy9zY2l0ZS0xLjYuMi93b3JrL3NjaW50aWxsYS9zcmMvTGV4TWF0bGFiLmN4eA==&lang=c%2B%2B)

---

### Post by Zugzwang on 2008-04-30
So there are already two GUIs for Octave: KOctave and QTOctave. How does your project relate to this? So is it really just syntax coloring?

To my mind, "interactive exploration" of the variables defined is one of the most important features (besides debugging) as it allows you to try what you want to do step-by-step first and them make an algorithm for it. You can of course simply type the name of the variable on the command line again each time, but that's quite tedious. Furthermore this variable view makes the whole thing a *lot* easier to understand for beginners.

---

### Post by ad_267 on 2008-05-01
This wouldn't be a gui for octave as such, it would just be adding support for Octave/Matlab to Geany. I don't want a big gui like qtoctave or koctave. At the moment I use octave with two terminals open, one for octave and one for vim. For other things like C or php I like to use Geany. Geany also allows you to execute the script you're working on in a terminal so for me it would be great being able to work on Octave/Matlab scripts in Geany.

---

