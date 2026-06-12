---
title: "Shutdown/restart not working 1st time."
date: 2013-02-03
forum: New to Ubuntu
---

### Post by d4m1r on 2013-02-03
Hey guys, I have been having this really weird problem for some time and I don't know how I can troubleshoot it....Basically, more and more often when I go to shutdown or restart my PC (from the top right menu), it does nothing :( It can sit there for 5-10 minutes, no additionally windows will pop up or anything. However, it automatically shutsdown/restarts when I go to the top right menu and select the same option immediately after.

It's a desktop, Ubuntu 12.04 LTS x64. Anyone have any idea's as to what's going on or troubleshooting suggestions? :confused:

---

### Post by cave2596 on 2013-02-04
Hello,

I had a simmilar problem.
I just reinstalled Ubuntu compleately.
Then it worked.

Hope, I could help you with that.

Greetings from Germany,
cave2596

---

### Post by d4m1r on 2013-02-04
Thanks for the reply but I do not want to reinstall the whole OS to fix this issue :???: Anyone have any idea's on how I could figure out why my PC is not immediately shutting down/restarting?

---

### Post by blackbird34 on 2013-02-04
Have you tried alternative shutdown methods? Here's the Terminal command:

```
sudo shutdown -h now
```If that works, it's some odd bug in the menu. In which case you could try a workaround by installing [Synapse]("https://apps.ubuntu.com/cat/applications/quantal/synapse/") (it's in the software centre): You do Control+Space to summon it, and if you type "shut down" into it, your computer should shut down pronto, and it's so much faster than the top-right menu that your problem won't really be one anymore :D

---

