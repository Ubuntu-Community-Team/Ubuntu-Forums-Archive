---
title: "Makes no sense; what is wrong here ?"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by Innernet on 2014-04-04
Hi all.
Installed a program for radiocommunications; could not find where is it hiding, then found as installed, but do not know how to make it run :confused:  Guidance and explanation, please ?

[ATTACH=CONFIG]251708[/ATTACH]

---

### Post by steeldriver on 2014-04-04
The message you are getting when you try to run the multimon software is  basically telling you that you haven't told it what file you want to  decode - it needs to be something like 'multimon myfile.wav' or whatever  - have a look at the manual page for details

```
man multimon
```

IIRC files don't show up in the dash search until the database gets updated  - by default, once per day, but you can force it by running 

```
sudo updatedb
```

from the command line.

---

### Post by elliotn on 2014-04-04
Correct answer above

---

