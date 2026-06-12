---
title: "Shell Script Question"
date: 2009-03-29
forum: Programming Talk
---

### Post by Tek-E on 2009-03-29
I was wondering is there a way to run a shell script in the background?

---

### Post by ghostdog74 on 2009-03-29
use  &

---

### Post by UbuKunubi on 2009-03-29
I've been using Python to automate a Terminal script.

There are lots of examples out there, but what I find to work is:

    f = os.popen("hcitool scan")#-----------Sends the command to the terminal
    for i in f.readlines():#-----------------Step through the list of information 

Hope this helps,
Ubu

---

