---
title: "How to SAVE etc. file before exiting Terminal"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by pdrusa on 2014-07-21
This will seem silly to some, but I really am a beginner.  Having attempted to install Java on my Ubuntu laptop and going through each step, the instructioins simply say to "save the etc. file and exit".  That is where I scratch my head in bewilderment -- how do I save a file in the Terminal?  The only answer I've found is to "press Escape, hold Shift and press the Z key twice" and that didn't work.  Help me, someone, please.

---

### Post by steeldriver on 2014-07-21
What terminal-based editor are you using to edit the file? can you post a link to the instructions that you're following?

---

### Post by pdrusa on 2014-07-21
I believe gedit is the editor, and the insructions are found at [URL="http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux"]http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux


[/URL]

---

### Post by pdrusa on 2014-07-21
Using the Gnome Terminal, 3.6.2

---

### Post by steeldriver on 2014-07-21
If you used gedit, it's a GUI editor and you can use regular mouse-based menu navigation to save and exit (although you could also use shortcuts Ctrl-S and Ctrl-Q if you prefer)

If you used the alternative nano editor (which *is* terminal based), then you can save with Ctrl-O (you will be prompted whether you want to overwrite the file - answer Y) and exit with Ctrl-X

---

### Post by yancek on 2014-07-21
> The only answer I've found is to "press Escape, hold Shift and press the Z key twice" 

Sounds like vi or vim editor.  The link below has information on it including options to save near the bottom of the page.  Hitting the Esc key is to get into command mode from insert mode.  You should also be able to save with-  :wq  then hit Enter.

[http://www.washington.edu/computing/unix/vi.html](http://www.washington.edu/computing/unix/vi.html)

---

