---
title: "Ubuntu (terminal) commands"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by new123 on 2011-10-02
I installed Ubuntu few days ago and works very good. "Ubuntu Software Center" works good for installing but not every application is in there, so some of them need to be installed manually.
When I need to install manually, I go to App's web site and see what commands to run (in terminal), but it confuses me because I don't even know what all those commands are for, all I know is it's about to install needed app, so I'm asking you, what those "sudo", "apt", "get", "add", "install update" "./configure" etc. do. (and if there are more usefull cmds, tell me), I just like having control on what's my PC is doing, that's why I switched from Windows to Linux. Atm, I would like if there is some "Ubuntu installer" like the "Windows installer", but maybe manually installing (and other stuff in terminal) could be even more fun if I know what commands that I running actually do.

---

### Post by dave01945 on 2011-10-02
the man page is probably going to be the best thing for you to read if you want to know what a command does just type in terminal

```
man *nameofcommand*

e.g.

man sudo
man apt-get
man apt
```

also **apropos** is a useful command that will search the man pages using a keyword so if you don't know the command you want you can search a keyword and it will list commands that contain the keyword

./configure is abit different that is used for compiling software from source this [**page**](https://help.ubuntu.com/community/CompilingSoftware) should explain more about that i would suggest not compiling from source until you have read abit more about it first

---

### Post by Frogs Hair on 2011-10-02
Hello and Welcome

If you stick to software from the Ubuntu software center or debian packages , known as (.deb ) you should not have to compile any software . There may be cases that the program you want doesn't come as a .deb package .

---

### Post by Neoncamouflage on 2011-10-02
```
sudo
``` - Things that require you to make significant or potentially dangerous changes require root or administrator level permission, Ubuntu prefers you don't simply run around as the root user, so sudo gives a command permission to do things for the root user. Putting it in a command basically tells the computer, "Yes, it's ok to do this".

```
apt-get
``` - Accesses the software repositories, a giant collection of various programs for Ubuntu users

```
apt-cache search "keyword"
``` - Searches through a stored list of programs in the repositories for your keyword. After the keyword, add ```
 | grep 'keyword'
``` to narrow down your results even more.

```
sudo apt-get install "package"
``` - Searches the repositories for the package specified and installs it, since it makes changes to your hard drive, sudo must be used.

```
sudo apt-get update/upgrade
``` - Both of these are used on a fairly regular basis, updates your repository information, any security updates, program patches, etc. Basic upkeep of your current software.

```
sudo apt-get remove "program"
``` - Removes a program from your system, leaving configuration files to be used if it is reinstalled.

```
sudo apt-get purge "program"
``` - Totally removes the chosen program from your system along with configuration files. Best thing if you know you won't be using that program again in the future.

I think that's really it for the basics of installing/finding/removing things with the terminal. I personally hate the software center, so this is how I install everything.

---

### Post by new123 on 2011-10-02
> **dave01945 said:**
> the man page is probably going to be the best thing for you to read if you want to know what a command does just type in terminal

```
man *nameofcommand*

e.g.

man sudo
man apt-get
man apt
```

also **apropos** is a useful command that will search the man pages using a keyword so if you don't know the command you want you can search a keyword and it will list commands that contain the keyword

./configure is abit different that is used for compiling software from source this [**page**](https://help.ubuntu.com/community/CompilingSoftware) should explain more about that i would suggest not compiling from source until you have read abit more about it first

Yeah, just tested the "man", it really shows detailed explanation, thanks it's great :) :)

---

### Post by wildmanne39 on 2011-10-02
Hi, here is some links and guides that will help.
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)
[http://linuxcommand.org/](http://linuxcommand.org/)
Thank you

---

### Post by new123 on 2011-10-02
> **Neoncamouflage said:**
> ```
sudo
``` - Things that require you to make significant or potentially dangerous changes require root or administrator level permission, Ubuntu prefers you don't simply run around as the root user, so sudo gives a command permission to do things for the root user. Putting it in a command basically tells the computer, "Yes, it's ok to do this".

```
apt-get
``` - Accesses the software repositories, a giant collection of various programs for Ubuntu users

```
apt-cache search "keyword"
``` - Searches through a stored list of programs in the repositories for your keyword. After the keyword, add ```
 | grep 'keyword'
``` to narrow down your results even more.

```
sudo apt-get install "package"
``` - Searches the repositories for the package specified and installs it, since it makes changes to your hard drive, sudo must be used.

```
sudo apt-get update/upgrade
``` - Both of these are used on a fairly regular basis, updates your repository information, any security updates, program patches, etc. Basic upkeep of your current software.

```
sudo apt-get remove "program"
``` - Removes a program from your system, leaving configuration files to be used if it is reinstalled.

```
sudo apt-get purge "program"
``` - Totally removes the chosen program from your system along with configuration files. Best thing if you know you won't be using that program again in the future.

I think that's really it for the basics of installing/finding/removing things with the terminal. I personally hate the software center, so this is how I install everything.

This is really nice explaining of thing I were asking for. Thanks alot.

---

### Post by new123 on 2011-10-02
Thank u all, I found solution in ur replies, so this is solved :) Peace

---

### Post by Neoncamouflage on 2011-10-02
Anytime. I know when I started learning this stuff all I wanted was a basic list of what the common commands were, and what they did. Seems fairly difficult to just get that from any of the help sites.

---

### Post by wildmanne39 on 2011-10-02
Hi Neoncamouflage, have a look at this PDF it is a great basic command list.
[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)
Thank you

---

### Post by ajgreeny on 2011-10-02
And finally:  As an alternative to **ubuntu-software-center** try **synaptic**.  It is a complete gui for apt-get, and though slightly more complicated to use than USC, it gives many more options and can help with broken packages etc etc.

Well worth a look, in my opinion.

---

