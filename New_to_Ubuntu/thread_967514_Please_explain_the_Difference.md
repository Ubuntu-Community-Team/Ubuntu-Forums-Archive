---
title: "Please explain the Difference"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by colcol on 2008-11-02
Hi sorry for asking what might seem logic/easy to you, but what is the difference between a terminal and a package manager, and am i right in thinking its the terminal you use to d/l and a package manager to install if someone could explain in simple English id be grateful and tell me where to find what is needed to carry out these tasks,:popcorn::confused: colcol

---

### Post by Sef on 2008-11-02
You type in commands in the terminal.   You can download and install from the terminal.

e.g., ```
sudo apt-get upgrade && sudo apt-get install package_name
```A package manager handles downloading and installing packages only.  

Synaptic is a package manager.   Add/Remove is a simplified version of Synaptic.

> Hi sorry for asking what might seem logic/easy to you

No need for apologies.  We like people here who are willing to learn.

---

### Post by scragar on 2008-11-02
The terminal is normaly more powerfull than the gui, and in many ways is faster.
```
sudo apt-get install **packageName**
```
will install the package without you having to wait for synaptic to start, then searching for the package, then clicking mark, and install, it's just so much faster to type a few letters and have it run.
And ```
apt-cache search **something**
``` is a very powerfull way of searching for a partial package, being about 300% more efficient than the search feature in synaptic.
```
apt-cache dump | grep **something**
```Will search for all packages who's names match a pattern(where the search option searchs descriptions and names), so it is normaly a fraction faster(and it's still many times faster than via synaptic).

---

### Post by kansasnoob on 2008-11-02
Look at this section:

> Install Software
Extra Repositories
File Permissions
Security in Ubuntu

Where's the Terminal?
Password in Terminal 

Of this guide:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

It's an all around great guide.

---

### Post by colcol on 2008-11-02
Thanks all ive give it a go downloaded songbird opened terminall entered sudo apt-get install songbird and got this

colcol@colcol-desktop:~$ sudo apt-get install songbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package songbird
colcol@colcol-desktop:~$ 

what am i doing wrong cheers colcol

---

### Post by Peter09 on 2008-11-02
Songbird is not in the repositories, hence the could not find it message.

---

### Post by ugm6hr on 2008-11-02
> **Peter09 said:**
> Songbird is not in the repositories, hence the could not find it message.

Indeed.

You can only install with apt if the application is in a "repository" that you have access to.

I think the start here link below would be useful to you - there are further links to installing app guides.

---

