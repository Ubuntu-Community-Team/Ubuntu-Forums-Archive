---
title: "How to change Terminal name thing"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by baker-quin on 2013-08-23
Hey in my Terminal I see this,

quinton@quinton-System-Product-Name:~$

whenever I go to type anything... I'm pretty sure this was a mistake of mine when installing. How do I change it?

---

### Post by tripp98 on 2013-08-23
That is the name of your computer when you installed ubuntu.

[http://askubuntu.com/questions/206698/changing-system-name](http://askubuntu.com/questions/206698/changing-system-name)

there is a link to the 2 things you have to change

---

### Post by deadflowr on 2013-08-23
> **baker-quin said:**
> Hey in my Terminal I see this,

quinton@quinton-System-Product-Name:~$

whenever I go to type anything... I'm pretty sure this was a mistake of mine when installing. How do I change it?

Yep, follow the link in the 2 post. 
Change /etc/hosts, and /etc/hostname(will need to be root), then restart.

It's a result of skipping over, and not paying attention to a line during installation.
when filling out your user info, it goes First Name,Last Name Computer Name, Username Password, confirm Password, various checkbox options(login, encryption, etc) and OK.
Because the Computer name line generates a name when you type your first name, most users don't think about changing it to something they'd prefer.

---

### Post by VMC on 2013-08-23
Do you want to change the 'host' name or Terminals display?

Edit: I see this is solved, but if you want to keep the 'hostname', and change the way Terminal displays a prompt. Look into '**PS1**', found in ~home. Edit '**.bashrc**'.

A good read is found [**here**]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html").

---

