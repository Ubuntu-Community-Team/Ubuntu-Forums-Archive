---
title: "[SOLVED] Remove Prompt when running a script"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Vyder on 2008-08-07
Hi

I wrote a really simple script to restart conky everytime i made changes to the .conkyrc file. But everytime i double-click the refresh-conky.sh file it asks weather to run it in terminal/display/cancel/run.

How do i change this so that if i double click the file it just runs it without asking me?

Cheers
Vyder

---

### Post by Rocket2DMn on 2008-08-07
You can create a launcher for the script which just calls the script.  Just right click the desktop or panel and Create Launcher, then give it the path to the script and run it as Application in Terminal (tho plain Application may work, too).  You may want to put the script somewhere out of the way if it is currently on your desktop, like move it somewhere appropriate in your home directory.

---

### Post by mcduck on 2008-08-07
Just take a look at the file manager's options. There is an option to select between opening the executable text fiels, running them or asking what to do..

---

### Post by Vyder on 2008-08-08
Thanks!

Don't know why I didnt think of using a launcher...

@mcduck found those options too...thanks

---

### Post by mcduck on 2008-08-09
edit: wrong thread :D

---

