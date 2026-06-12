---
title: "Controlling Ubuntu's windows"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by ph34r on 2008-11-30
I have been messing around with Ubuntu for a bit now and I know there must be a way to fix this, but I can't seem to find it.

I can't figure out how to make it so that applications I close (firefox window, apps windows, etc.) open back up where I last closed them.  This is highly annoying, and if I can figure it out would make me really love Ubuntu.  Since 7.10 all my windows always open up in annoying default positions in the corners of my screen.  Trying to search for a solutions always leads me to dual-boot posts since the word "windows" is in my question.

p.s.  I know there is probably a blatantly obvious way to correct this, sadly for me the more obvious the answer the harder it is to find it XD

---

### Post by ets2006 on 2008-11-30
you should be able to tweak that somewhere in gconf-editor -i put a launcher on my tray for gconf-editor so that i can tweak gnome whenever i hant to!

go to terminal and run gconf-editor
it should be somewhere in the tree, if i find the exact location i will post.

---

### Post by ets2006 on 2008-11-30
apparently, gnome does remember startup postitions. (if it does it doesn't do it very well)

see [this link]("http://ubuntuforums.org/showthread.php?t=146296") for more information.

---

### Post by ph34r on 2008-11-30
Thank you very much for you help.  I'll give that link a try :)

---

### Post by ph34r on 2008-11-30
From what I read in that link, and following some others, is that gnome says for the apps to handle start-up positions.  And that if my apps chose not to handle it I'm more or less left high and dry.

---

### Post by whitethorn on 2008-11-30
I know this isn't exactly what you were asking about.  But there are ways of telling windows to start up where you want them to.  Not quite the same as remembering where it was when you closed it.  If you use compiz, you can use the 

Place Windows

plugin, and if you're using Metacity you can use devilspie.  Which is in synaptic.

---

