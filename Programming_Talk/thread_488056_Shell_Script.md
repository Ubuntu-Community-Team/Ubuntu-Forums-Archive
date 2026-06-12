---
title: "Shell Script"
date: 2007-06-29
forum: Programming Talk
---

### Post by phizikal on 2007-06-29
I have this game, am I want to make a shell script that "cd" my "Desktop" and "wine NittoLegendsBeta.exe" without having to do it through the shall manually. Just click and run. :D

---

### Post by phizikal on 2007-06-29
I found a nice tutorial, but can anyone make me a quick one until i can learn shell scripting? [http://www.hackerthreads.org/phpbb/viewtopic.php?t=714](http://www.hackerthreads.org/phpbb/viewtopic.php?t=714)

---

### Post by HackingYodel on 2007-06-29
Wouldn't something like this work?
```
#!/bin/sh

wine ~/Desktop/NittoLegendsBeta.exe
```

and then **chmod +x** the file and it'll give you the option to run it when double clicked.

---

### Post by phizikal on 2007-06-29
Yeah that works, I can't find no good articles on shell scripting.

---

### Post by HackingYodel on 2007-06-30
> **phizikal said:**
> Yeah that works, I can't find no good articles on shell scripting.

Here is one I like a lot.  [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

