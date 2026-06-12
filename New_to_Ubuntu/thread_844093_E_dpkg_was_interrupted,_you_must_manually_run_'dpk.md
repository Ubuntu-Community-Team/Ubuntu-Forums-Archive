---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by mavic on 2008-06-29
I've tried to install new updates from Synaptic but it comes 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried to install the new available updates from the term ( so if I'm not missing from manually) but it also came the same script. What should i do???
Thanks for reading and helping.

---

### Post by lswest on 2008-06-29
If you read the error carefully, it usually presents a solution, in this case: "you must manually run 'dpkg --configure -a' to correct the problem."

Basically run this command: ```
sudo dpkg --configure -a
``` in the terminal and it will solve your problem, if not, post back.

---

### Post by mavic on 2008-06-29
Thank you very much!! But also in each terminal " code" there are the advises of what you should ???

---

### Post by Elfy on 2008-06-29
Perhaps you could post one of the terminal messages so we can see what you mean.

---

### Post by lswest on 2008-06-29
> **forestpixie said:**
> Perhaps you could post one of the terminal messages so we can see what you mean.

seconded, I'm not entirely sure what you mean, could you maybe give us an example?

And thanks for the thanks, glad I could help.

---

### Post by skarly94 on 2008-06-29
I just started using Ubuntu, and when I try to add wine this comes out:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I go to terminal and put in 'dpkg --configure -a' 
then this comes out: dpkg: requested operation requires superuser privilege.



Can anyone help??

---

### Post by Elfy on 2008-06-29
Read the thread again - the answer is in post 2.

---

### Post by helliewm on 2008-06-29
You need to type sudo before the command

Application, Accessories, Terminal

In the terminal type

 sudo dpkg --configure -a.

It will ask you for your password, type it press return and let it do its stuff.

It will not let you install anymore programmes until you have done this. So don't try installing Wine or anything else.

---

### Post by lswest on 2008-06-30
the reason the command in the error message doesn't have "sudo" before it is because the command you ran ("sudo apt-get install wine") already is being run as super-user (or synaptic, you entered your password before trying to install, right?) Therefore the error message shows you what you would need to type **if** you were still the root user (super-user).  Basically, it assumes you're still the root user since the command you ran before had a sudo (however, sudo only affects the command directly after it).  Just fyi.

---

### Post by willgrimes on 2008-07-01
I have the same problem.  I used the sudo command and I enter my password.  It still come back to requesting superuser.  Ok, how do I get to be a superuser or how do I get around this problem?

---

### Post by sayakb on 2008-07-01
At a terminal, type in:
```
sudo bash
```
And then fire up **dpkg --configure -a**

---

