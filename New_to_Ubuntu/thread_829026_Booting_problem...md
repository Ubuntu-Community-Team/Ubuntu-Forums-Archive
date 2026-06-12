---
title: "Booting problem.."
date: 2008-06-14
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-06-14
Yesterday i installed Windows XP pro SP2 in a new hard disk with a new SATA and POWER cable.

After installation i have worked
When i worked my system got freeze and my mouse pointer moved very slowly.
I finished my work  and shut down my system.

then today morning i switched on my system
i got the error message "A disk Read error" press "CTRL+ALT+DEL" to restart.

then once again i tried to do fresh install windows XP ..

during setup it had copied all the files and restarted to install xp but when my system restarted its shows the windows XP loading page then an blue screen came after that no process carried on its still shown the empty blue screen

One my friend insisted me to install Ubuntu.

I tried installing Ubuntu freshly
and successfully installed. now i didn't get any error message.

now ubuntu is working properly without any error message while loading.

now this is the situation.
What is the problem?
please help me out to solve the problem

---

### Post by rraj.be on 2008-06-14
Is your problem is your windows not booting right?

Could yo be a bit more clear.

Try fsck in terminal to check any hard disk error.

---

### Post by jimbren on 2008-06-14
I don't understand the question...I assume you're trying to install Ubuntu and Windows XP alongside one another.  The second time around, you had a clean install of XP and then did a clean installation of Ubuntu.  Both should be working properly.  

Is one of them not working?

---

### Post by sxytrillian on 2008-06-14
when i installed windows xp it didnt work.

then i installed ubuntu its working.

now what is the problem with xp?

---

### Post by rraj.be on 2008-06-14
What happens when you boot into windows.

Is it still showing you the blank blue screen.
[If so,It means that the installation is corrupted.]

---

### Post by ukripper on 2008-06-14
> **sxytrillian said:**
> Yesterday i installed Windows XP pro SP2 in a new hard disk with a new SATA and POWER cable.

After installation i have worked
When i worked my system got freeze and my mouse pointer moved very slowly.
I finished my work  and shut down my system.

then today morning i switched on my system
i got the error message "A disk Read error" press "CTRL+ALT+DEL" to restart.

then once again i tried to do fresh install windows XP ..

during setup it had copied all the files and restarted to install xp but when my system restarted its shows the windows XP loading page then an blue screen came after that no process carried on its still shown the empty blue screen

One my friend insisted me to install Ubuntu.

I tried installing Ubuntu freshly
and successfully installed. now i didn't get any error message.

now ubuntu is working properly without any error message while loading.

now this is the situation.
What is the problem?
please help me out to solve the problem

If ubuntu is working on your system then I see no problem with ubuntu working.

---

### Post by nicfallenangel on 2008-06-14
> **sxytrillian said:**
> Yesterday i installed Windows XP pro SP2 in a new hard disk with a new SATA and POWER cable.

It sounds like the Windows XP SATA driver was corrupted. XP does not natively support SATA, you need a third party driver to run on most SATA boards. Unless you really need Windows to run something that doesn't run in linux, I would just enjoy the Ubuntu fun.

---

