---
title: "Updater will not work"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by JSF16 on 2012-10-29
Okay, new problem cropped up a while ago, namely that my Update Manager can't check for updates. Picture included below, I have no idea what's going on.

---

### Post by twipley on 2012-10-29
Hello John-Sir-Frank the sixteenth,

One thing you might try, is firing up the following from the terminal:
```
gksudo gedit /etc/apt/sources.list
```
, then remove or add a # to the beginning of both of those lines.

Tell us how it went!
twipley

---

### Post by Bashing-om on 2012-10-29
Hi ! JSF16;

I am sure you did check the obvious, that your internet connection is working.

Can it be that the server for your mirror site is down ? Change mirrors:
open software center -> top screen task bar ->edit->Software Sources;
in the screen that opens up is a window: Download From , click the arrow, follow prompts and accept the recommended mirror site, apply to update your data base.
(this is for version 12.04)

please advise on the results. <== BDQ

---

### Post by deadflowr on 2012-10-29
For the graphical way, as opposed to post #2.
In the updater, click on settings, go to other software, locate the offending ppa(s) and uncheck them. Then close and click check to run the update again.

---

### Post by JSF16 on 2012-10-29
I need more detailed instructions to help in the Terminal solution. What lines do you refer to? There are many lines.

Switching mirrors did naught, and I'm unsure if there are any offending ppas (screenshot included)

---

### Post by twipley on 2012-10-29
pmcenery ones, of course.

nice ppa porn, by the way. ;)

---

### Post by JSF16 on 2012-10-29
Pmcenery? 

And what ppa porn?

---

### Post by deadflowr on 2012-10-29
Yes, uncheck the ppa's for pmcenery, as it hasn't been updated since natty narwhal.

[https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=]("https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=")

---

### Post by JSF16 on 2012-10-30
Success, thank you.

---

