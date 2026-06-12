---
title: "sudo command not working."
date: 2012-02-18
forum: New to Ubuntu
---

### Post by mojdave on 2012-02-18
[SIZE=2]Hello.[/SIZE]

[SIZE=2]I am  fairly new user to linux/Ubuntu ( i know ) and getting the hang of it . I have some basic knowledge about terminal and few related commands  and from what i gather , one needs to use sudo command along with apt to install any application in this os unlike windows[/SIZE].

[SIZE=2]That's where the problem begins , when i try to enter sudo-add-apt .... it gives the following message

" sudo: unable to change to sudoers gid: Operation not permitted "

gathering from the various sites on this topic i get that this command is supposed to work as root substitute for normal users (like myself) ,so as not to delete any important file by accident in root.So  how am i supposed to access this command for a fresh install of ubuntu 11.10 ?[/SIZE]:confused:

---

### Post by iangarforth on 2012-02-18
> **mojdave said:**
> [SIZE=2]Hello.[/SIZE]

[SIZE=2]That's where the problem begins , when i try to enter sudo-add-apt .... it gives the following message

" sudo: unable to change to sudoers gid: Operation not permitted "
[/SIZE]:confused:

Umm, I'm as new as you, chap, but 'sudo' always has a space after it, not conjoined by a modifier like -

Don't know if that's it, or if I am, in fact, completely wrong...

---

### Post by winh8r on 2012-02-18
> **iangarforth said:**
> Umm, I'm as new as you, chap, but 'sudo' always has a space after it, not conjoined by a modifier like -

Don't know if that's it, or if I am, in fact, completely wrong...

you are correct Iangarforth!


the correct syntax is 

sudo apt-get

or sudo <command>  with a space after the word sudo.

---

### Post by clive littlewood on 2012-02-18
Hi

I would ask why are you using Sudo to install.

Just go to the software centre or synaptic package manager find the program you need and install.

Why make things difficult ?

Clive

---

### Post by iangarforth on 2012-02-18
Dear Diary,

Today I got my first ever thing right on Ubuntu Forums...  A good day :-)

---

### Post by HavarN on 2012-02-18
You are not limited to using apt-get to install new software. There is a lot of alternatives. However these are the most used ones.

Terminal commands:
```
aptitude
dpkg -i downloaded_package.deb
```Replace downloaded_package.deb with the filename of your downloaded .deb package.

aptitude is similar to apt-get.

GUI:
```
synaptic
Ubuntu Software Center (software-center)
```
synaptic is more advanced than the software-center.

However, all programs that install software require super user rights, which they gain if you add *sudo* or *gksu* and a space in front of the command.

---

### Post by forrestcupp on 2012-02-18
> **clive littlewood said:**
> Hi

I would ask why are you using Sudo to install.

Just go to the software centre or synaptic package manager find the program you need and install.

Why make things difficult ?

Clive

Hey guys. He didn't say he was trying a **sudo apt-get...** He said he tried a **sudo add-apt...**, and the "..." probably means "add-apt-repository". He was probably trying to add a PPA, and didn't realize that sudo doesn't have a hyphen after it.

Sometimes when you're following directions someone gives you, it's easier to copy commands than to try to figure out the same thing on your own in an easier GUI.

---

