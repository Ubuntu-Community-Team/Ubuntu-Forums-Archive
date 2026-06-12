---
title: "[SOLVED] Synaptic package manager error"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by neonjuice on 2008-11-21
Hi.

I am using Ubuntu Intrepid and today I got an error when trying to access the Synaptic package manager. Here is the error I received.

E: dpkg was interrupted, you must manually run ' dpkg --configure -a ' to correct the problem. E: _cache->open()failed,please report.


I have been using Linux now for must be 3 weeks or so and feel I am getting the hang of it. This however throw me.

I went into th terminal and tried to run the instructed code. It says I need super user permissions to run the command. I am the admin on my machine. I am unsure of exactly how to solve this problem. I searched but found no exact match to my problem.

Hope you guys can help.

Thank you

---

### Post by Sitting Duck on 2008-11-21
Try

> sudo dpkg --configure -a

sudo gives you super user status

---

### Post by Michael.Godawski on 2008-11-21
Sitting Duck is right; 

usually this error occurs when a installation or update process was interrupted or terminated without being completed. 

Has the sudo command worked?

---

### Post by neonjuice on 2008-11-21
Yes it sure worked. Thank you very much.

I had been typing Sudo run and then the command.. I thought you had to put the run in to get it to work. My mistake.

---

