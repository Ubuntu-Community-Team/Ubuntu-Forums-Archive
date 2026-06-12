---
title: "IntelliJ"
date: 2006-08-09
forum: Programming Talk
---

### Post by melkor12 on 2006-08-09
Hi, 
I am quite new to Ubuntu. I have recently downloaded the intelliJ program and  run idea.sh from the .../intelliJ/bin directory. Then, I entered my licence information and intelliJ IDEA started working. After a while, I closed it but now I can't find a way to start it again. I have looked at /usr/bin but can't seem to find it.
Any suggestions?

---

### Post by melkor12 on 2006-08-10
anyone?

---

### Post by sphinx on 2006-08-10
It depends where exactly you ran idea.sh from. You say you installed it from ../intellij/bin but that is only a relative path. Not an exact one.

A command to tell you what directory you are currently in is 'pwd'.

At a guess the binary you need to run will be in the ../intelliJ/bin/idea-[some number]/bin directory.

Note: [some number] is the build number of that particular release of intellij I beleive.

Hope I've helped.

---

### Post by depele on 2006-12-31
I think intelliJ is a bit slow on ubunutu.
I would like to get it smootly running.

We use it in school so it would be nice if I could use it @ home (under linux) so I can practise my programming skills.

---

### Post by pmasiar on 2006-12-31
eclipse is another java IDE, it is free and opensource, you may want to try it

---

### Post by Ramses de Norre on 2006-12-31
This should reveal it's location:
```
locate idea.sh
```

---

### Post by PigCorpse on 2006-12-31
Okay

<IntelliJ directory>/bin/idea.sh

If that doesn't work (gives an error about JRE)...

nano idea.sh

And you have to add a new line at the beginning (between the two blocks of comments is good) that goes:

IDEA_JDK=/usr/lib/jvm/java-1.5.0-sun

Edit the version number to suit.

---

