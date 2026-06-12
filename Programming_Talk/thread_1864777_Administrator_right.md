---
title: "Administrator right"
date: 2011-10-19
forum: Programming Talk
---

### Post by papaapa on 2011-10-19
Hello!

I am writing a simple java application which executes another command with "sudo". My application works properly when i start it with "sudo my_java_application". But if i start it without sudo it does not works. And it does not ask me for password. It gives error when it executes the command. It gives: "you have not the permissions". What should i write to source of my java program to get (ask) the "sudo" rights?

If i get the right how often i need to get again to execute this command. Because my program executes the command every 10-15-20-25  minutes (sometimes more long, it depends something else) automatically.

Thank you!

---

### Post by Bachstelze on 2011-10-19
Use gksudo instead of sudo.

---

### Post by papaapa on 2011-10-21
I don't know why but my java based program could not start . It does not give me an error. It does not start. And it works perfect with sudo 'my_app.jar'.

Anyway but i am asking here, how to ask for administrator rights from user?
I need code...

---

### Post by nvteighen on 2011-10-21
No. Please, don't hardcode the program to call sudo/gksudo on its own. What if the system is configured to use su/gksu? And also, doing so produces a secondary problem, which is, you now how to deal with the program asking for the password, without you having any control on what happens next.

First, check out if you can't get the same functionality from some library or module, so that you can control the things it does.

Second, if root privileges are needed, make the user choose to do that. Write the shell call without sudo, so that if the user wants it to run as root, he'll have to explicitly do so.

Third, there's a way to interface PAM through a library (Kerberos?), such that you get a "custom" gksu/gksudo functionality that works only for your program, but I'm not sure how it works...

---

### Post by papaapa on 2011-10-21
> **nvteighen said:**
> No. Please, don't hardcode the program to call sudo/gksudo on its own. What if the system is configured to use su/gksu? And also, doing so produces a secondary problem, which is, you now how to deal with the program asking for the password, without you having any control on what happens next.

First, check out if you can't get the same functionality from some library or module, so that you can control the things it does.

Second, if root privileges are needed, make the user choose to do that. Write the shell call without sudo, so that if the user wants it to run as root, he'll have to explicitly do so.

Third, there's a way to interface PAM through a library (Kerberos?), such that you get a "custom" gksu/gksudo functionality that works only for your program, but I'm not sure how it works...

For now it is not problem to call sudo because the program wrote by me and it just makes a very simple thing.

My program can not ask password (like software center, synaptic package manager...) when my program executes a command which needs administrator right. Because i don't know the java API to do that. That is my problem.

---

### Post by ofnuts on 2011-10-21
> **papaapa said:**
> For now it is not problem to call sudo because the program wrote by me and it just makes a very simple thing.

My program can not ask password (like software center, synaptic package manager...) when my program executes a command which needs administrator right. Because i don't know the java API to do that. That is my problem.I don't think there is. But this means you should reconsider your design. Your application, as a whole, needs privileges, so it should be started in a sudo. You can also package it differently, and have a user-level process talk to some system-level daemon..

---

