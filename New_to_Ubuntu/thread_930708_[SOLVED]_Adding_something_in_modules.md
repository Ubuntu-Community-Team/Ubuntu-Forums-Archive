---
title: "[SOLVED] Adding something in modules"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by MrBalll on 2008-09-26
I was told I need to add ath9k into my etc/modules. I am not too sure how to access the modules or how to add something into them. If someone could help me with this I would appreciate it. Thanks.

---

### Post by wolfen69 on 2008-09-26
in terminal: ```
gksudo nautilus
```then just copy and paste the file into the directory.

---

### Post by jamesrl on 2008-09-26
(see below)

---

### Post by jamesrl on 2008-09-26
/etc/ is a directory that stores configuration files specific to your machine (not just your user).

/etc/modules is a text file containing a list of modules

So run (Alt-F2)
```

gksudo /etc/modules

```
and you can edit the text file and add ath9k to it (the gksudo is to give yourself permission to edit the file as it isn't in your home directory).

---

### Post by MrBalll on 2008-09-26
TO wolfen69-
Alright, that popped up the root File Browser, but I don't understand how to add a line. What the user said to me was "Then go into your etc/modules and add a line that says: ath9k"

How would I go about adding the line? Thanks.

To jamesrl-
After I ran that command it asked for my password so I typed it in and then nothing else happened. Am I missing something?

---

### Post by silverglade00 on 2008-09-26
Jamesrl's command should have been
```
gksudo gedit /etc/modules
```

Then go to the end of the file and type

ath9k

and press enter. It's not always necessary to end a configuration file on a blank new line, but I found out the hard way that sometimes the system doesn't like it, so I just got into the habit of doing it.

---

