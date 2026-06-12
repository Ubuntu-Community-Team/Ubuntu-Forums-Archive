---
title: "Making a directory with the help of todays date"
date: 2005-09-26
forum: Programming Talk
---

### Post by dilerra on 2005-09-26
Hi all,

I'm really frustrated. I'm new into piping, and I cannot seem to get some fairly simple stuff to get working. I want to create a folder with todays date.

To get the date i enter "date +%F". Now I'd like to redirect the output to the command "mkdir", kind of like "date +%F | mkdir"... but this doesn't work.

Any clues on how to get past this simple task? :)

/ M

---

### Post by mlomker on 2005-09-26
**mkdir $(date +%F)**

---

### Post by bkasterm on 2005-09-26
I don't know how to use a pipe, but

mkdir `date +%F`

does the job.

Best,
Bart

---

### Post by rsay on 2005-09-26
Try 

mkdir $(date +%m_%d_%y)

You should be able to start from this. You can use "man date" for more parameters if you need them.

---

### Post by dilerra on 2005-09-27
[QUOTE=mlomker]**mkdir $(date +%F)**[/QUOTE]

This was exactly was I was looking for. Now maybe I will get that backup script up and running in a few minutes :D

Thanks!

---

### Post by jerome bettis on 2005-09-27
advanced bash scripting guide, pdf
[http://www.tldp.org/LDP/abs/abs-guide.pdf]("http://www.tldp.org/LDP/abs/abs-guide.pdf")  (right click -> save as)

a few weeks ago i sucked at bash and thought it was messy.  after reading a few chapters of that, i kind of like it.

---

