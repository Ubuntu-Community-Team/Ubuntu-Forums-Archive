---
title: "sudo or gksudo or su"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by richardfv on 2008-04-27
hello, i am new at ubuntu, i used to use suse and mandriva a litte before, however when trying to get few things done i have to use or sudo or gksudo and sometimes none of them are working, i am using ubuntu 8 with kde so i guess kubuntu... any suggestions

usually the error message shows as

sudo: unable to resolve host frederick-laptop

might be permission pb, in that case how and where to change this...

thanks in advance, ps ubuntu looks great

---

### Post by master5o1 on 2008-04-27
I have always used sudo in terminal, gksu in terminal for opening a gui program and su for switching user.

eg.

Opening nano in terminal with sudo permissions:
```
sudo nano /etc/apt/sources.lst
```

Opening gedit in terminal with sudo permissions:
```
gksu gedit /etc/apt/sources.lst
```

Switching to another user:
```
su mark
su jason
su ...
```

Switching to root user:
```
sudo su root
```
(because root is disabled by default, it has no password of any kind. Only way to access root is sudo su root command to give you root privileges to run the su root command to then make you root for a longer session.

---

### Post by hums07 on 2008-04-27
In KDE, to launch graphical application with root privilege, use
```
kdesu
```
for terminal application use
```
sudo
```

So openning /boot/grub/menu.lst from terminal:
```
kdesu kate /boot/grub/menu.lst
```

---

### Post by bodhi.zazen on 2008-04-27
The "calssic " links :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)


If you want a root shell, I advise you use ```
sudo -i
```

---

### Post by richardfv on 2008-04-27
well thats my point, i thought so too, howerver none of them gives me permissions, channel told me this might be sources.list issue, in that case how can i solve this

---

### Post by richardfv on 2008-04-27
> **hums07 said:**
> In KDE, to launch graphical application with root privilege, use
```
kdesu
```
for terminal application use
```
sudo
```

So openning /boot/grub/menu.lst from terminal:
```
kdesu kate /boot/grub/menu.lst
```


well thats my point, i thought so too, howerver none of them gives me permissions, channel told me this might be sources.list issue, in that case how can i solve this

---

### Post by bodhi.zazen on 2008-04-27
It is hard to tell from your description of the problem.

Can you open a terminal and enter sudo ls ? when asked for a password enter you log in password (you will not see anything on the screen) and press enter. Post the terminal output, including any error message.

Repeat with kdesu kate ...

Potential problems include : wrong password (are you trying a root rather then a user password ?),  are you in the admin  group (enter "id" , w/o quotes, in a terminal) ? , did you change your hostname ?

It seems telling us it is not working has not been descriptive enough.

---

### Post by richardfv on 2008-04-27
> **bodhi.zazen said:**
> It is hard to tell from your description of the problem.

Can you open a terminal and enter sudo ls ? when asked for a password enter you log in password (you will not see anything on the screen) and press enter. Post the terminal output, including any error message.

Repeat with kdesu kate ...

Potential problems include : wrong password (are you trying a root rather then a user password ?),  are you in the admin  group (enter "id" , w/o quotes, in a terminal) ? , did you change your hostname ?

It seems telling us it is not working has not been descriptive enough.

fred@frederick-laptop:~$ sudo ls
sudo: unable to resolve host frederick-laptop
fred@frederick-laptop:~$ gksudo ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
fred@frederick-laptop:~$ kdesu kate
kbuildsycoca running...
sudo: unable to resolve host frederick-laptop

fred@frederick-laptop:~$
fred@frederick-laptop:~$ kdesu
kbuildsycoca running...
ASSERT: "i <= nodes" in /usr/share/qt3/include/qvaluelist.h (376)
Launched ok, pid = 7172

---

### Post by bodhi.zazen on 2008-04-27
Reboot your computer , at the grub screen select recovery mode.

you will be a a command line only interface, but you will be root

Use nano , an editor.

```
nano /etc/hosts
```make sure your hostname listed on the line with 127.0.0.1 is frederick-laptop

> 127.0.0.1 localhost frederick-laptopNow Ctrl-X to exit, type y to save if you made any changes.

Then

```
nano /etc/hostname
```That should have a single line 

> frederick-laptopNow, last of all, 

```
groups <user_name>
```where <user_name> is your log in name , make sure you are listed in the admin group.

If not, 

```
nano /etc/groups
```Add your username at the end of the line in the admin group.

Reboot. That *should* fix the problem.

---

### Post by richardfv on 2008-04-27
> **bodhi.zazen said:**
> Reboot your computer , at the grub screen select recovery mode.

you will be a a command line only interface, but you will be root

Use nano , an editor.

```
nano /etc/hosts
```make sure your hostname listed on the line with 127.0.0.1 is frederick-laptop

Now Ctrl-X to exit, type y to save if you made any changes.

Then

```
nano /etc/hostname
```That should have a single line 



Now, last of all, 

```
groups <user_name>
```where <user_name> is your log in name , make sure you are listed in the admin group.

If not, 

```
nano /etc/groups
```Add your username at the end of the line in the admin group.

Reboot. That *should* fix the problem.

did the trick, at last it works fine,  thanks for your help.

---

