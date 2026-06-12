---
title: "Use of command line to start GUI"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by sammykur on 2014-04-13
I have read several pages about the use of the command line for starting a GUI and have read conflicting information

My question is this

If troubleshooting a program should you use the command line to start a program with a GUI or not??/ and if so should you use gksudo or just plain sudo with the -v switch ??

---

### Post by Double.J on 2014-04-13
Hi there!


in case anyone hasn't said so yet, welcome to the community!


to answer your question, it may be better to look at the difference between starting a graphical program with sudo and gksudo. After all, why are their 2? Well if you launch with gksudo, it loads the root configuration. If you use sudo, it loads your configuration with root access. Sounds good? True but you can end up changing the ownership of configuration files on your profile to root user only. This would be bad.


gksudo does have the -d option for debugging?


Jj

---

### Post by buzzingrobot on 2014-04-13
The suggestion to launch a GUI program via a command line is due to the possibility that if launched in a terminal, the program will display error messages that are not displayed when launched in the usual GUI manner. If gksudo is used, the app will launch in the usual manner and those error message won't be generated, or won't be seen if they are.

You would only need to preface the command with "sudo" if it needs root privileges to run.

---

### Post by vasa1 on 2014-04-13
> **buzzingrobot said:**
> ... If gksudo is used, the app will launch in the usual manner and those error message won't be generated, or won't be seen if they are.

You would only need to preface the command with "sudo" if it needs root privileges to run.
1: errors are also seen with gksudo. Actually, there's no reason that I know of why gksudo should suppress or hide these messages.
2: it is suggested that launching GUI programs with higher privileges is better done with gksudo/gksu rather than sudo. There are reasons suggested for that. If I find a link I'll post here. AFAIK, sudo isn't recommended for opening GUI programs with elevated privileges.

---

### Post by sammykur on 2014-04-13
Sorry for the delay in getting back- Thank you all
It seems to best practice to run gksudo for a gui and use the -d option
The pages i was reading were about gparted and troubleshooting it. so you did in fact need elevated privileges to run it.
sorry about the -v switch i was thin thinking it was for verbose,not validate

---

### Post by buzzingrobot on 2014-04-13
Applications can be aware of the environment in which they are launched and generate messages appropriate to that environment.

GTK spps -- don't know about QT apps -- will often complain about missing GUI resources if launched from a terminal.  Some do not like being launched as root, which also triggers error messages that are probably not related to the problem at hand.

---

