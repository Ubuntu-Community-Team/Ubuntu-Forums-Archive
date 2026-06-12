---
title: "[SOLVED] Making and Saving Changes to Conf Files"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by yojimba on 2008-08-15
Making changes to Mediaprobe.conf file using gedit (simply by locating the file in a file manager and double clicking to open and make changes). 

I have made the changes with gedit but can't save the changes to the original file. 

I understand using sudo to save from the terminal. But is there a way to save the conf file from within the gedit gui so I don't have to open the terminal and mess with all the directory commands?

---

### Post by Crafty Kisses on 2008-08-15
You can do the following to save in the Terminal:
```
Cntrl+W
```

---

### Post by daimaru on 2008-08-15
you can open terminal and enter 
```
sudo nautilus
```that way you start the window manager nautilus as root and you can browse to your conf files and edit them with gedit etc. and it will save since your using root level access.

---

### Post by dje on 2008-08-15
from the terminal or alt + f2 (run dialog):
```
gksu gedit /path/to/conf file
```

dje

---

### Post by yojimba on 2008-08-15
> **daimaru said:**
> you can open terminal and enter 
```
sudo nautilus &
```that way you start the window manager nautilus as root and you can browse to your conf files and edit them with gedit etc. and it will save since your using root level access.

Thank you. This is what I was after so I wouldn't have to save the long file locations. However, ss there anyway to do it without having to log on as root?

---

### Post by dje on 2008-08-15
> **yojimba said:**
> Thank you. This is what I was after so I wouldn't have to save the long file locations. However, ss there anyway to do it without having to log on as root?

no because you need root permission to edit the files ;)

dje

---

### Post by yojimba on 2008-08-15
> **dje said:**
> no because you need root permission to edit the files ;)

dje

Was hoping there might be some way to use the sudo command I guess. :)

---

### Post by daimaru on 2008-08-15
> **yojimba said:**
> Was hoping there might be some way to use the sudo command I guess. :)
well you kind of are using it. you're just sudoing the window manager nautilus which equals using it with root access. so its no different than editing your conf file with a sudo command from terminal.
EDIT:
changed the command to sudo nautilus without running it in background with the & sign, cause i just tried and mine did not work with the & attached .

---

### Post by dje on 2008-08-15
also best to use gksu with graphical applicatons:
```
gksu nautilus &
```
[reason why]("http://www.psychocats.net/ubuntu/graphicalsudo")

dje

---

### Post by yojimba on 2008-08-15
Thanks so much. Bummer is now I'm using Catfish within Nautilus to find the file and am getting a 'fatal error, search was aborted' :confused:

---

### Post by yojimba on 2008-08-15
Good to go! Thanks again!:guitar:

---

### Post by daimaru on 2008-08-16
> **dje said:**
> also best to use gksu with graphical applicatons:
```
gksu nautilus &
```[reason why]("http://www.psychocats.net/ubuntu/graphicalsudo")

dje
thanks for the info dje. I never experienced problems with sudo so i sometimes used gksu and sometimes sudo. from now on I'll stick to using gk for graphical stuff. 

one more question . is gksu an alias for gksudo ? or is there a difference too between the two?

---

### Post by ingeva on 2008-08-16
> **daimaru said:**
> thanks for the info dje. I never experienced problems with sudo so i sometimes used gksu and sometimes sudo. from now on I'll stick to using gk for graphical stuff. 

one more question . is gksu an alias for gksudo ? or is there a difference too between the two?

AFAIK one is a link to the other, so in practice they should be identical.

However, su and sudo are different.

---

