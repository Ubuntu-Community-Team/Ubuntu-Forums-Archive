---
title: "showing progress for mv, cp, etc"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-09-29
I use cp and mv a lot to move large files and groups of files.  Is there a way to view the progress, or a script that would show me how close the transfer is to being done?

---

### Post by Primefalcon on 2008-09-29
mv -v file/folder file/folder

-v means verbose btw you can use it with a lot of commands

---

### Post by shortridge11 on 2008-09-29
-v just tells me what i'm doing.  I'm looking for an actively updated progress bar or percentage.

---

### Post by shortridge11 on 2008-09-30
if that's not possible to do, please let me know.  I'd rather know something can't be done then think someone hasn't told me how yet.

Thanks

---

### Post by jerome1232 on 2008-09-30
I don't see a way to do that, if you want to find out more about the options you can give these commands check our their man page
```
man cp
man mv
```

---

### Post by KIAaze on 2008-09-30
It is possible!
I saw it somewhere. let me try to find it again. :)

---

### Post by jerome1232 on 2008-09-30
You are right!
Looks like you have to patch the programs and recompile them though.
[http://ubuntuforums.org/showthread.php?p=2061158](http://ubuntuforums.org/showthread.php?p=2061158)

---

### Post by nothingspecial on 2008-09-30
[http://ubuntuforums.org/showthread.php?p=2061158](http://ubuntuforums.org/showthread.php?p=2061158)

Not done this myself so use at own risk.

---

### Post by shortridge11 on 2008-09-30
sorry jerome- that was the first place i looked =\.  There doesn't seem to be a (built in) way to view the progress of moving/copying large files in any manual.

---

### Post by KIAaze on 2008-09-30
That's the one I remember:
[http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/](http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/)

And here some others I found while googling:
[http://www.linuxquestions.org/questions/linux-general-1/cp-progress-bar-407381/](http://www.linuxquestions.org/questions/linux-general-1/cp-progress-bar-407381/)
[http://www.theiling.de/projects/bar.html](http://www.theiling.de/projects/bar.html)

Ok, so it's not "directly" possible with mv or cp, but scripts can be written to do it.
Just place the scripts in /usr/bin or /usr/local/bin and you can use them like any other command. :)

P.S: The "midnight commander" suggested on the linuxquestions.org thread also seems interesting.
It allows mouse input!

---

### Post by shortridge11 on 2008-09-30
that's what i was looking for!  Many thanks!

---

### Post by shortridge11 on 2008-10-01
KIAaze- yours is by far the easiest way

---

