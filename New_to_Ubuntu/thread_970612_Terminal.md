---
title: "Terminal"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by huwaw69 on 2008-11-04
[CENTER]I don't know if this is the right question but i just wanna know the answer

i used terminal a lot of times but i don't really understand what im typing there i just type what is in this forum and what i see...

1st question: What is terminal
2nd question: What the hell is sudo?
3rd question: why use terminal?
4th question what is apt?

i hope im not bothering and i hope im asking the right question in the right forum...[/CENTER]

---

### Post by taurus on 2008-11-04
1 & 3 -- [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
2 -- [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
4 -- Just type "man apt" in a terminal for a manpage.

---

### Post by redDEADresolve on 2008-11-04
I find that when I don't know something about Ubuntu or Linux, I hit up [www.wikipedia.org](www.wikipedia.org)


[http://en.wikipedia.org/wiki/Computer_console](http://en.wikipedia.org/wiki/Computer_console)

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

---

### Post by bodhi.zazen on 2008-11-04
This link also helps :

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by bhadotia on 2008-11-04
Simple answers (as far as I understand):

1. A terminal (emulator) is program that put a window before you which is like the old terminal consoles which were used to operate computers when there was no GUI. 
2. sudo is a command which allows you to have full access to your system. It is similar to su (though not the same). When you use the command :
```
sudo apt-get install conky
```
you are telling the system to install the program conky, but in linux you can install software only if you are root (the super-user account which has full access to the system) and the sudo commands tells the computer to run the command that follows it as that user (and therefore asks you for your password).
3.No great reason to use terminal if you have great hardware. But whatever the case may be terminal is always faster than GUI. And there are some programs for which the GUI front-ends have not yet been created- so you are bound to use the terminal for them.
4. APT is  the package management system used by debian-based linux distros. It manages the install, dependency and upgrade of the software you install on your system.

[Here]("http://gd.tuwien.ac.at/linuxcommand.org/") is a good link to learn the terminal and have some basic knowledge of the linux OS. There is another link in ,my signature (though not well organized but written in an attractiv style).

---

