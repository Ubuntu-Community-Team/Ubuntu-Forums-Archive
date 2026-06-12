---
title: "Why won't a script file run?"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by bdemers on 2008-10-19
How do I go about determining why a script won't run?  I posted a question earlier about how to figure out why a link doesn't work.  Both are in the same directory.  I haven't an answer to the link issue yet, maybe this will help some?

---

### Post by The Cog on 2008-10-19
"doesn't work" leaves a world of possibilities. How are you trying to run it, and what error message do you get?

Check that it is executable - look at the permissions.

---

### Post by bdemers on 2008-10-19
Well, absolutely nothing happens.  No messages, no smoke, no catcalls, nutt'n.  So question is what's it's supposed to do?  Frankly I don't know for sure.  The purpose of the file is to allow me to generate an electronic symbol for use in a program called gschem.  Gschem is a schematic drawing program.  It is part of a suite called gEDA. tragesym is the script file (from above)name and it is a python file, I believe.  The tragesym how-to page tells me to run the file.  It is an exe, so I double click and, well, loop to top of this paragraph.

---

### Post by BDNiner on 2008-10-19
Can you post the commands you are typing and the errors you are getting. the instructions on: [http://www.geda.seul.org/wiki/geda:tragesym_tutorial](http://www.geda.seul.org/wiki/geda:tragesym_tutorial) seem pretty straight forward.

It is not an exe file so double clicking on it is not going to do anything. you need to execute the file from a terminal window according to the instructions on their page.

---

### Post by TideMan on 2008-10-19
Perhaps only rank novices like myself would think to suggest the following, because only a novice would make such a mistake:

I had the same problem the other day with fdisk
```
fdisk -l
```
gave me nothing at all.  What I found I needed to do was:
```
sudo fdisk -l
```

---

