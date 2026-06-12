---
title: "root password"
date: 2023-08-28
forum: New to Ubuntu
---

### Post by jsdata on 2023-08-28
Hi,

I'm new to Ubuntu and Linux. Should I do anything with the 'root' user password on my new installation ? 
Should I reset it ? Set it ? Change it ? 
IF I change it, does it mean thet I have to type it every time I get new updates ?

Cheers.

---

### Post by deadflowr on 2023-08-28
Basic understandings of root and sudo on Ubuntu:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Rubi1200 on 2023-08-28
Hi and welcome to the forums :-)

By default, the root account is locked on Ubuntu for security reasons. The password you were prompted to create during installation is what allows you to have elevated privileges for a limited amount of time in order to perform actions which would normally need root access.

For example, if you want to update the system, install software etc. you would need elevated permissions. On Ubuntu this is known as sudo and is reserved for use by administrators of the system.

There is no need to change this password, unless you don't think it is secure enough.

Also be aware that you should almost never run graphical applications as the root or sudo user; it is a major security flaw and could break your system.

Read the information in the link posted by deadflowr and if you still have questions, feel free to ask us.

---

### Post by jsdata on 2023-08-28
Thanks for fast response. I better leave the 'root' user and continue with other new issues O:)
@Rubi1200 - 'Also be aware that you should almost never run graphical applications as the root or sudo user', does it mean that such as auto updates shold be scriptet instead of setting it in the GUI ? :-s

---

### Post by ajgreeny on 2023-08-28
There are some GUI applications that are meant to run as administrator only such as synaptic package manager, which is installed by default on some of the DE versions, eg, Xubuntu.

If you go to that in the menu system you will automatically be asked for your user password.

For most other GUI apps it is not a good idea to use sudo.

---

### Post by grahammechanical on 2023-08-28
> Also be aware that you should almost never run graphical applications as  the root or sudo user; it is a major security flaw and could break your  system.


A little explanation, if I may.

Ubuntu  sits on top of a computer operating system called Linux which is  controlled through commands. Ubuntu allows us to issue Linux commands  when we load the Terminal. If we know the right commands we can load the  file manager (Files) and an editor (Text Editor - also called gedit)  with elevated or root privileges. If we do not know what we are doing we  can do a lot of damage to the operating system and our documents. Linux  commands are very powerful. With elevated privileges and limited  understanding we can make the operating system unusable. So, we are  given fair warning.

Incidently, when we load Software Updater and  give it authority to do its work Software Updater will run some Linux  Commands. Through the terminal we can run those commands individually  and directly. 

Utilities with a Graphical User Interface make it  easier to work with Linux and at the same time avoid breaking the  operating system.

Regards

---

### Post by jsdata on 2023-08-28
... meaning that I rather should use commands
[FONT=courier new]sudo apt-get update
sudo apt-get upgrade[/FONT]
in the CLI

---

### Post by Impavidus on 2023-08-28
The GUI tools meant for administrative tasks, like update-manager, synaptic etc., all have a clean way built in to manage root privileges. There's absolutely no problem using those. Those tools are designed to be safe. The issue is when you use ordinary tools like text editors or file managers with root privileges. Those don't (all) come with the additional safeguards to protect your system. The tools with a GUI are typically worst.

---

### Post by jsdata on 2023-08-28
I usually work in tools like Visual Studio Code and Notepad++
I expect that these have the logged in user's privilegies

---

### Post by MAFoElffen on 2023-08-28
> **ajgreeny said:**
> There are some GUI applications that are meant to run as administrator only such as synaptic package manager, which is installed by default on some of the DE versions, eg, Xubuntu.

If you go to that in the menu system you will automatically be asked for your user password.

For most other GUI apps it is not a good idea to use sudo.
Sort of. The wording of that might imploy that they are only run as root, which would cnofuse the OP, when they actually are not.

They are meant to run by a user, started with elevated permissions. For example, to start the synaptic package manager or gnome-disks you can start them from the command line via
```

sudo -H synaptic
# Or along the lines of...
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY synaptic

```
and when  you start the graphically, the desktop files ask for sudo crendentila to run as a user with elevated permissions.

It does run a root, and the audit trail still tracks as a User using sudo...

---

### Post by jsdata on 2023-08-28
... and thanks to @deadflowr for the
 Basic understandings of root and sudo on Ubuntu:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

