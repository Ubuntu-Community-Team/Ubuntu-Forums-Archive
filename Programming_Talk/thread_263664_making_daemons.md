---
title: "making daemons"
date: 2006-09-23
forum: Programming Talk
---

### Post by wildseven on 2006-09-23
anyone have any advice on making a daemon to open ports and have it listen? i'm not a programming guru, but i have experience in java and sadly VB.

---

### Post by dhpe on 2006-09-23
You may read general information about daemons at [wikipedia]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29").

If you want a daemon to listen to a port, you should look for socket functionality. The programming language does not play a big role here - - use what ever supports your needs.

---

### Post by Orestes on 2006-09-23
I have had great joy with socket programming in python.

type ```
pydoc socket
``` into a terminal for specifics, and there's loads of goodies on the web to help you out.

I know that to code a daemon, you have to fork a process off that goes on to do the work while the original process dies. This is how, when you run a daemon from BASH, it drops back to the BASH prompt instead of chugging along like a program does. I also know that python supports forking, however I've never written a true daemon in python.

HTH

---

