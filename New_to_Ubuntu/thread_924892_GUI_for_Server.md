---
title: "GUI for Server"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by nyihtut100 on 2008-09-20
I am new to Ubuntu -- i like to used Ubuntu much than windows
but i have some questions

1. can i install Ubuntu Desktop on Windows Vista?
   if yes which software to used it and how to install?

2. can i install Ubuntu Server on Windows Vista?
   if yes which software to used it and how to install?

3. can i install Ubuntu Server on Ubuntu Desktop?
   can i install Ubuntu Desktop on Ubuntu Server?

the most important things is how to change the Server to GUI mode?

---

### Post by quinnten83 on 2008-09-20
Hey,
your questions are a bit incomprehensible.
Do you mean the following:
- you have a computer with Vista installed, but you also want to install ubuntu on this same computer and be able to choose which operating system to
use when you start the computer? 
The answer to this is yes, the installation process of Ubuntu will walk you through it, but make a backup!!!!




If you mean that you want ubuntus interface on your vista. I don't think that is possible. 

if you have a server installation, you can install the desktop environment of ubuntu so everything is gui:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Shazaam on 2008-09-20
1. Yes. It is called a WUBI install. It is like normally installed software in Windows meaning you can go to Add/Remove Programs in Windows and uninstall it. There is a subforum for it here. Later on if you find that you like Ubuntu you can convert your WUBI installation into a normal hard drive install.
2. Not sure.
3. The difference (besides a few software changes) between the Desktop version and the server version is that the server version does not have a pre-installed desktop (graphical user interface). You can always change the server version to a desktop one by installing the meta package ubuntu-desktop. It will be harder to go the other way (Desktop to Server).

---

### Post by zvacet on 2008-09-20
If you install desktop version you can have server too with going to the **synaptic>edit tab>mark packages by task>LAMP**.

---

### Post by airtonix on 2008-09-20
> If you install desktop version you can have server too with going to the **synaptic>edit tab>mark packages by task>LAMP**.

LAMP = Linux Apache Mysql Php. Which means installing those components doesnt make your ubuntu install the same as the server version of ubuntu. 

For one your not using the server kernel which at 32bits can handle more than 4gbs of ram.

---

### Post by Trebaruna on 2008-09-20
> **quinnten83 said:**
> 
if you have a server installation, you can install the desktop environment of ubuntu so everything is gui:

```
sudo apt-get install ubuntu-desktop
```
This also installs the desktop kernel, openoffice and a slew of other programs. My server tells me it would need to download 1777MB to install [FONT=Courier New]ubuntu-desktop[/FONT] and its dependencies.
You might want to try [FONT=Courier New]gnome-core[/FONT] or [FONT=Courier New]kde-core[/FONT] instead. These packages provide a basic desktop with a file browser and text editor, but do not require all of Ubuntu's default desktop to be downloaded and installed. Of course, you might want something more lightweight, in which case perhaps [FONT=Courier New]xfce4 [FONT=Verdana]would do the job.[/FONT]
[FONT=Verdana]
As for installing "on Vista", you can either dualboot:
[/FONT][/FONT][https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
or you can install with Wubi, as mentioned by Shazaam.

Even if it is possible to install server on Vista (I don't know whether it is), you have to ask yourself why you'd want to. A server is meant to run continuously, usually without user intervention, whereas wubi is designed to allow users to interact with Ubuntu from within Windows. If you need a server, you most likely do not want wubi. If you want a desktop with a server core, perhaps it might work for you; if wubi is available for server, that is. Unfortunately I only have a 64 bit image and only a virtualbox windows image, so I cannot test.

---

### Post by zvacet on 2008-09-20
@ **airtonix**

> For one your not using the server kernel which at 32bits can handle more than 4gbs of ram.

You are right,but is so hard to go to the synaptic and install server kernel?

---

### Post by nyihtut100 on 2008-09-21
thank you to all - i like to know another things
when i install
sudo apt-get install ubuntu-desktop
that one is take about 540MB more to download its take long time for me
my internet connection is very slow
is this ubuntu-desktop is the same as Ubuntu Desktop version?
or is only for server to used with GUI?

---

