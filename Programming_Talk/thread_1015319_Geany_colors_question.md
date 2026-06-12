---
title: "Geany colors question"
date: 2008-12-18
forum: Programming Talk
---

### Post by JaxDragon on 2008-12-18
I have Geany installed, but how do I change the background color of the editor?

---

### Post by ZuLuuuuuu on 2008-12-18
Unfortunately you have to edit configuration files:

[http://www.geany.org/manual/current/index.html#configuration-files](http://www.geany.org/manual/current/index.html#configuration-files)

---

### Post by DirtDawg on 2009-02-18
Hi. This is an old thread, but I wanted to clear this up for people who may be looking for a way to use a darker theme. It's easy! 

First, download the dark theme from [this page]("http://code.google.com/p/geany-dark-scheme/").

Next, unzip the package you downloaded. Inside you'll find lots of files with names like "filetypes.python" and "filetypes.html." Now simply copy/paste these files into ~/.geany/filedefs/ 

EDIT: As of Geany version 0.16, paste said files into ~/.config/geany/filedefs/ 

You can either copy/paste all these files to effect everything you open, or only selected files, say filetypes.html to effect only html files.

Next time you start Geany, you will have a dark theme. :D

---

### Post by swappo1 on 2009-06-21
Anybody try this with Geany 0.17?  I am not able to get the dark background to work following these instructions.  It worked on my laptop a few months ago when I changed the background but I don't know what version it was.  Any ideas how to get this to work?

---

### Post by monguin61 on 2009-07-04
[sorry.. no idea about the 0.17 issue...]

I have a couple of problems with geany -

1. I can't seem to make any changes to colors for .conf files - I've edited filetypes.conf in both ~/.config/geany/filedefs AND /usr/share/geany, and none of the colors change. I check the Document>Set Filetype option in the menu, and it does say "Config file"

2. I can't get geany to automatically recognize files like .alias and .bashrc as .sh files, so I have to set the filetype manually every time I open them.

Has anyone else had these problems? Any idea how to resolve them?

---

### Post by Porter200el on 2009-10-09
you need to change the owner to yourself of the following directory: 

/usr/share/geany

1. open terminal
2. cd /usr/share
3. sudo chown username:username geany


Then paste the files in and restart geany.  I would make a copy of all the original files first, so you can restore it if you don't like the dark theme.

---

### Post by Sporkman on 2009-10-11
Works great, thx. :)

I didn't like the current line highlighting, but it was easy to figure out how to change that, as the config files are well documented.

---

