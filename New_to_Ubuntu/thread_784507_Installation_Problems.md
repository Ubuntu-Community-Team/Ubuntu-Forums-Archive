---
title: "Installation Problems"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by kevb8ll on 2008-05-06
I've alluded to this in another post - but thought I would say it as a seperate.

I have tried installing a number of programs / utilities using add/remove programs KDE.

Some have installed, but most haven't, although when I try to install again - it says it has.

I have gone to the appropriate folder (system etc) to check - but nothing.

Can someone give some advice to a newbie of how I can check where programs are etc.

I have 8.04 and using KDE4

Thanks.

---

### Post by justifier on 2008-05-06
try starting them from terminal, does this work?.

e.g. you install kopete, in terminal try typing kopete

---

### Post by kevb8ll on 2008-05-06
Thanks for the prompt reply. I'm willing to try it - How can I do that please.

The key thing I want to install is startup manager

---

### Post by justifier on 2008-05-06
have you installed it yet? if so open up a terminal (cant remember the path in KDE apps > terminal maybe? and type startup-manager otherwisem install a small program, like kopete and see if that comes into the menu's if not try the terminal approach (type kopete and hit enter)

---

### Post by kevb8ll on 2008-05-06
Loads of errors, here is the last bit:

/usr/share/startupmanager/gtk_frontend.py:174: Warning: invalid (NULL) pointer instance
  gtk.main_iteration()
/usr/share/startupmanager/gtk_frontend.py:174: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  gtk.main_iteration()
Segmentation fault

That was from the root in konsole

---

### Post by justifier on 2008-05-06
from root? or the standard user?

---

### Post by kevb8ll on 2008-05-06
Root

---

### Post by justifier on 2008-05-06
try running it as a standard user, NEVER run programs as root unless absolutly nessicary

---

### Post by kevb8ll on 2008-05-06
But it told me I wasn't authourised. :-(

---

### Post by SunnyRabbiera on 2008-05-06
> **kevb8ll said:**
> But it told me I wasn't authourised. :-(

in that case try typing in sudo before your command.

---

### Post by kevb8ll on 2008-05-06
This is what I got:

kevin@home-PC:~$ sudo startup manager
[sudo] password for kevin:
sudo: startup: command not found
kevin@home-PC:~$ sudo startup-manager
sudo: startup-manager: command not found
kevin@home-PC:~$

I tried both spellings of startup manager, but as you can see it didn't work.

BTW - I DID put my admin password in.

---

### Post by justifier on 2008-05-06
try 
```
startupmanager
```

otherwise 

```
sudo apt-get install startupmanager
```

---

### Post by kevb8ll on 2008-05-06
[QUOTE=justifier;4897426]try 
```
startupmanager
```

That did it - I didn't realise I'd put a space in, what a muppet!

Now a question, this doesn't install the program does it? It isn't anywhere to be found still. I assume this just allows me to run it once.

(I've updated my boot order now though).

---

### Post by justifier on 2008-05-06
if its not in your menu's and you want it to be just  right click, > create menu item (or words to that effect) and put that in as the command to use in terminal, asi say i dont know the exact way in KDE, there might be a simpler way but thats a pretty generic way, glad you have it running now!!

---

