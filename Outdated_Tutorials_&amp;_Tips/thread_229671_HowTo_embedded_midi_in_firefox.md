---
title: "HowTo: embedded midi in firefox"
date: 2006-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Peturrr on 2006-08-04
[B]Info
[/B]Midi files aren't working in firefox without a special plugin and ofcourse a midi software 'renderer'. 
The plugin doesn't cooperate very nice with Acrobat Reader in firefox, but using xpdf in firefox solves this problem.

[B]Installation
[/B]Open up a terminal and execute
```
sudo apt-get install timidity mozplugger
``` Answer yes to all questions and the installation will be complete.

Restart firefox (don't forget to close all instances) and voila, embedded midi files should now play.

**if pdf's arent displaying anymore in your browser because of this, you can solve it by doing the following:**
```
sudo apt-get install xpdf
``` ```
sudo gedit /etc/mozpluggerrc 
``` Put an # before the line with acroread in it, as shown below.
```
text/x-pdf: pdf: PDF file
#      repeat swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"
        repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
        repeat noisy swallow(gv) fill: gv --safer --quiet --antialias -geometry +9000+9000 "$file"

```

---

### Post by glennric on 2006-08-13
Thanks.  The only thing is why does mozplugger not work with acroread?

Edit:  Nevermind.  I figured out how to make acroread work with mozplugger.
See
[http://www.ubuntuforums.org/showthread.php?t=186701]("http://www.ubuntuforums.org/showthread.php?t=186701")

---

### Post by drx on 2007-10-21
I am using Feisty and this istallation hint will not work. :/ Firefox complains that it did not find an applicable plugin for audio/midi.

Are there any other prerequisites apart from these two packages? (Freepats for example is needed for timidity.)

---

### Post by DagMan on 2007-10-22
I think you would need freepats and timidity both.  This worked fine for me in Feisty btw, and in Gutsy, except that I never mess around with Acroread since mozpluger makes good use of other lighter pdf tools as well.  Also in gutsy I have to hit play on pages that show a play pause and stop thing where they played automaticaly before and in another Linux.

---

### Post by stefanauss on 2007-11-03
> **drx said:**
> I am using Feisty and this istallation hint will not work. :/ Firefox complains that it did not find an applicable plugin for audio/midi.

Are there any other prerequisites apart from these two packages? (Freepats for example is needed for timidity.)

You need to delete /home/[USERNAME]/.mozilla/pluginreg.dat and restart firefox. This is because a bug require mozplugger to be the last plugin loaded (and it will be if you delete that plugin file).

---

### Post by ocheyes on 2007-12-12
I can't find pluginreg.dat to delete it. I've look in a few places. Can somebody tell me its correct location? I'm using ubuntu 7.10

---

### Post by wally the duck on 2008-02-09
There is a mozilla folder in your Home folder, but you cannot see it until you turn on 'show hidden files' in the 'view' menu.

---

