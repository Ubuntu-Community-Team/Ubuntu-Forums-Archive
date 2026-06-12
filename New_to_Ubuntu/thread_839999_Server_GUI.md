---
title: "Server GUI"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by rickferd on 2008-06-25
How do I get a gui interface in ubuntu server edition. Is it there and I just don't know how to start it, or can I install Gnome or something?:confused:

---

### Post by sam_delta on 2008-06-25
you will need to install it.
btw, basically, ubuntu desktop = ubuntu server + gui + default aplications

you can install gnome, but as it is a server, the gui isnt the most important part, so a lighter desktop will be better, 

just wait few mins before everyone start droping suggestions
sam

---

### Post by bluepowder7 on 2008-06-25
why do you need a gui on a server?  my file server at home doesn't have a monitor, keyboard, or mouse hooked up to it, and i just connect to it and perform settings and stuff via terminal and ssh.

maybe an option would be a web-gui of some kind?

---

### Post by rickferd on 2008-06-25
I am a windows person I am not that good at the CLI yet and would like to start useing it and then start to move to the CLI slowly. Also I am old and it takes me a little nit of time to adjust to new things.

---

### Post by lazyart on 2008-06-25
sudo apt-get install ubuntu-desktop
or
xubuntu-desktop
or
kubuntu-desktop

Yes, it's normally frowned upon to load a desktop enviroment onto a server, but it's your machine.

---

### Post by hyper_ch on 2008-06-25
> **rickferd said:**
> I am a windows person I am not that good at the CLI yet and would like to start useing it and then start to move to the CLI slowly. Also I am old and it takes me a little nit of time to adjust to new things.

Better start to learning it immediately... you know, setting up a server is usually done by editing config files and I don't see a difference in editing config files in nano or gedit.

Basic commands you need to know:
- how to move around your filesystem hierarchy --> cd
- how to list files --> ls
- how to edit files --> nano (or vi or .....)
- how to re/start services --> sudo /etc/init.d/SERVER restart
- how to install software --> sudo apt-get install package
- how to search for software --> sudo apt-cache KEYWORDS

That's all the cli commands you normally use for setting up a server...

---

### Post by rickferd on 2008-06-25
alright I got the desktop installed using 
sudo apt-get install ubuntu-desktop

this will also work for kubuntu-desktop too.

Thank You for the help

---

