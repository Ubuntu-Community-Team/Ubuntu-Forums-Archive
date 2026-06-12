---
title: "Simple Program: Terminal Shortcut"
date: 2006-10-19
forum: Programming Talk
---

### Post by tonyr1988 on 2006-10-19
My Situation: I commonly SSH into our college computers (two different addresses). I know I'm lazy, but it's a pain to type in my username and the fairly long addresses, especially since I can't tab-complete them.

My Solution (I think): Could I have a simple program to add a function (like "connect", since it's unused on my machine) that would automate the ssh'ing? For example, I could do:

connect -a (to connect to [email]myusername@aaaa.rest.of.addr[/email]ess)
connect -b (to connect to [email]myusername@bbbb.rest.of.addr[/email]ess)

The addresses would be hard-coded. I have experience in some languages (PHP, C, etc), but have no idea where to start. How would I accept the arguments -x? And will it prompt me for my password afterwards like normal, or will it not work as planned?

Simple program, uber-small, no real value to anyone except me, I just need guidance on how to start.

Thanks!

---

### Post by tonyr1988 on 2006-10-19
Scratch that - I just realized that I could create an alias for a custom command of my own. MUCH easier! :)

PS How do I delete this thread?

---

### Post by dean703 on 2006-10-19
Looks like a job for a shell script to me. Look at this page for a reference: 
[http://www.cyberciti.biz/faq/how-to-use-ssh-in-unix-or-linux-shell-script/](http://www.cyberciti.biz/faq/how-to-use-ssh-in-unix-or-linux-shell-script/)

---

