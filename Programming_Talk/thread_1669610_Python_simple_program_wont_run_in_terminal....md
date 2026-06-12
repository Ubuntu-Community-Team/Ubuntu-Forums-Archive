---
title: "Python simple program wont run in terminal..."
date: 2011-01-18
forum: Programming Talk
---

### Post by Synergy_N9 on 2011-01-18
Hello All,

My first post here on the Ubuntu Forums. Hope I found the right place for this question.

I have a simple program I am trying to run in the terminal.
[PHP]
x = raw_input("Enter name: ")

print "Hey " + x

raw_input("Press<enter>")
[/PHP]The py file is in a folder on my desktop I double click the file then select Run in Terminal.
Terminal opens but so fast I can't see the program.
The program works in the Python Shell and another system(not Ubuntu), and I am pretty sure it used to work for me in Ubuntu.

Useing IDLE 2.6 and Ubuntu 10.04.

Thanks Ron

---

### Post by endotherm on 2011-01-18
well, first off, you need a bangline to tell the shell what interpretor to use.
put this at the very top of your file:
```
#!/usr/bin/env python
```try creating a launcher for your script (rclick the desktop) and set it for "Application in Terminal"

---

### Post by Synergy_N9 on 2011-01-18
endotherm,

Wow that did it. Also created a launcher on the desktop. Learning a lot today. 

Thanks

Ron

---

### Post by Arndt on 2011-01-18
> **endotherm said:**
> well, first off, you need a bangline to tell the shell what interpretor to use.
put this at the very top of your file:
```
#!/usr/bin/env python
```

Not the shell, to be exact, but the kernel. No shell need be involved.

---

### Post by Synergy_N9 on 2011-01-18
Arndt,

Got it kernel not shell. Makes more scene.

Thanks
-Ron

---

