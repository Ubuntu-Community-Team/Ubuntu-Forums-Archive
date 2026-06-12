---
title: "startup applications doesn't work"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by qreapster on 2013-05-26
Hello everybody, i have tried to make htop a startup application, but it does not seem to work.
Since i want htop to start in workspace 1 in fullscreen i had also tried to install 'gdevilspie' (failed eventho i installed the pyhton script as bugs report said), so since i wasn't able to get any help from any other posts i decided to make a user (probably a good idea since im kinda new to ubuntu).

I am running ubuntu 13.04

Screenshot from the startup application (i have tried the commands "htop" and as you see there "gnome-terminal -x htop"):
[ATTACH=CONFIG]243074[/ATTACH]

Thank you very much :)

---

### Post by ajgreeny on 2013-05-26
I don't know anything about gdevilspie, but in xubuntu you can start **xfce4-terminal** with the **--fullscreen** option to the command, or  **--maximize** if you prefer.
Perhaps the same is true of gnome-terminal.

If not perhaps you can start with the **--hide-menubar** option or the **--geometry=###x###** to get the terminal size you want, though why htop is not starting I can not imagine, as it starts fine from a standard launcher on my Xubuntu 12.04 system, so I presume it would also do so from **Startup applications**.

---

### Post by qreapster on 2013-05-26
I tried the "--maximize/--fullscreen" command in terminal but it just starts and shuts down.
Thank you very much for your answer tho, i hope somebody else knows anything about this :)

---

### Post by qreapster on 2013-05-26
> **qreapster said:**
> I tried the "--maximize/--fullscreen" command in terminal but it just starts and shuts down.
Thank you very much for your answer tho, i hope somebody else knows anything about this :)
Also if anybody knows how to make a startup script that would execute **htop** in fullscreen @workspace 1 that would fix my problems totally! :)

---

