---
title: "'cp' progres bar?"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by CrewDK on 2013-02-19
Sometimes I need to copy\move rather big files (e.g. couple GB's or more) through bash script. Every time I must sit and wait thinking "how many time remains?..." 
Is there any way to see some sort of progress bar for this action, like in `mc` for example?

---

### Post by thermion on 2013-02-19
As far as I know, there's no progression bar in cp.
You can use *cp -v* to know what *cp* is actually doing.

[Something like this might work for you]("http://www.linuxquestions.org/questions/linux-general-1/cp-progress-bar-407381/")

---

### Post by oldos2er on 2013-02-19
You can use pv: [http://www.commandlinefu.com/commands/view/5107/copy-a-file-using-pv-and-watch-its-progress](http://www.commandlinefu.com/commands/view/5107/copy-a-file-using-pv-and-watch-its-progress)

---

