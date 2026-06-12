---
title: "[SOLVED] CPU usage percentage high all the time"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-01
System Monitor shows my CPU is constantly above 90%. What do I need to check to find out what is causing this.

FYI this is a Intel 3.06 gigHz Cidermill (Celeron) CPU. There is 1 gig of RAM.

---

### Post by vikram on 2008-10-01
> **Mark_in_Hollywood said:**
> System Monitor shows my CPU is constantly above 90%. What do I need to check to find out what is causing this.

FYI this is a Intel 3.06 gigHz Cidermill (Celeron) CPU. There is 1 gig of RAM.

In the terminal type the "top" command to view usage by different processes.

---

### Post by jamesrl on 2008-10-01
From the command prompt type in top, and you can see which processes are running. 

If you want a slightly fancier version of top, install htop (color and selectable menus).
```

sudo apt-get install htop
```

---

### Post by ajgreeny on 2008-10-01
In a terminal type ```
top
```and see what the output shows as using the cpu.  By default the cpu usage is how the display is sorted so the major user will be at the top of the list that shows.

EDIT:  OK, too slow!

---

### Post by Mark_in_Hollywood on 2008-10-01
top shows that Origami is using over 80% of resources. Origami is the Folding at Home project that does math on proteins that cause cancer. It's supposed to run in the background between every other process.

I've decided to remove it and ask the author what's the problem. Thank, community.

---

### Post by jakupl on 2008-10-01
... nevermind.

I was too slow.

---

### Post by Mark_in_Hollywood on 2008-10-06
I got the solution to this through another thread:

[http://ubuntuforums.org/search.php?searchid=49158370](http://ubuntuforums.org/search.php?searchid=49158370)

thanks, community.

---

