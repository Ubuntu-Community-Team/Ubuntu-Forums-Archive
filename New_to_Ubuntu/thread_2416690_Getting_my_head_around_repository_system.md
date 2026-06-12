---
title: "Getting my head around repository system"
date: 2019-04-13
forum: New to Ubuntu
---

### Post by likewise2 on 2019-04-13
I am new to Linux and new to Ubuntu as well. I am presently a windows user who is trying to migrate to linux.

As you can understand I am comfortable working with programs and not repositories. I mean how will I know that a specific program will need a dependency and needs a new group to install. Should I just type 'apt-get search' or 'apt-cache search'? I am have many queries regarding this. If anybody will direct me to a tutorial or such sort that can clear my idea about repositories then it will be very helpful.

---

### Post by oldos2er on 2019-04-13
> **likewise2 said:**
>  how will I know that a specific program will need a dependency and needs a new group to install

APT will take care of dependencies for you, that's one of its functions. See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu), and [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Not sure what you mean by "needs a new group to install."

*apt search <keyword>* makes for a bit less typing. If you'd rather have a GUI, try synaptic: ```
sudo apt install synaptic
```.

---

### Post by kc1di on 2019-04-13
Hello likewise2 and Welcome to Ubuntu forums, 

The apt package manager does a great job of finding dependencies for you and when you install a package it will install all need dependencies with it.  
For instance say you want to install VLC  all you have to do in the terminal is type```
sudo apt install vlc
``` and it will install vlc and all dependencies that are needed to make it run.  I suggest installing synaptic as one of the first programs as that is a graphical use front-end for apt and dpkg.  Then you can just search synaptic for the programs you want and install them through that.  Or you can also use the software center.  One thing with linux is you will have choices. 
[URL="https://help.ubuntu.com/lts/serverguide/package-management.html.en"]
This page[/URL] may be of help in understanding how it works. 

and [this page]("https://www.pontikis.net/blog/package-management-system-update-ubuntu-desktop") also. 
Enjoy the learning curve you'll be a pro before you know it :)

---

### Post by deadflowr on 2019-04-13
apt handles dependecies for you.
To start it's best to use programs such as synaptic or the software center (Software in Ubuntu).
They are both graphical applications for managing applications.
(Though you'll find synaptic to be more verbose in what it provides in details)

The system has manuals built into it for apt/apt-get (run man apt or man apt-get to view the man pages.)
More on apt here:
[https://help.ubuntu.com/community/AptGet/Howto]("https://help.ubuntu.com/community/AptGet/Howto")
[https://help.ubuntu.com/lts/serverguide/apt.html.en]("https://help.ubuntu.com/lts/serverguide/apt.html.en")

Some references on repository basics here:
[https://help.ubuntu.com/community/Repositories]("https://help.ubuntu.com/community/Repositories")
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
[https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

### Post by likewise2 on 2019-04-14
Okay, so basically my package manager will take care of all the dependencies which in this case is apt. Although I can see that there are two types of commands one is apt and another one is apt-get (or in some cases apt-cache). Are they different?

---

### Post by Bashing-om on 2019-04-14
likewise2; Hello -

apt-get is in the process of being depreciated in favor of apt.
see:
[https://mvogt.wordpress.com/2014/04/04/apt-1-0/](https://mvogt.wordpress.com/2014/04/04/apt-1-0/)
[https://itsfoss.com/apt-vs-apt-get-difference/](https://itsfoss.com/apt-vs-apt-get-difference/)
[http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/)

[INDENT]my bit to try and help
[/INDENT]

---

### Post by likewise2 on 2019-04-14
> **Bashing-om said:**
> likewise2; Hello -

apt-get is in the process of being depreciated in favor of apt.
see:
[https://mvogt.wordpress.com/2014/04/04/apt-1-0/](https://mvogt.wordpress.com/2014/04/04/apt-1-0/)
[https://itsfoss.com/apt-vs-apt-get-difference/](https://itsfoss.com/apt-vs-apt-get-difference/)
[http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/)
[INDENT]my bit to try and help
[/INDENT]


Wow, its really amazing. I bet more people will like it now.;)

---

### Post by DuckHook on 2019-04-14
Apt is a program used to not only install packages but keep their dependencies in sync. This is very important because we do not want various packages to drag in incompatible dependencies. There are other apps that can act as front ends or replacements for Apt, but they work on the same principle. Advanced users like using Apt because it is powerful, flexible and can be invoked with short commands that pack a lot of punch into a concise string of characters. Also because it is guaranteed to be on every flavour, so it's a know common denominator. But it is rather arcane, especially for new users.

If you prefer a GUI alternative, try Synaptic. It's much more newbie friendly, although it must be said that anything dealing with packages and installations will start out with a large measure of complexity. Can't be helped. After all, we are dealing with what constitutes the guts of the system. It requires exposure to the messy, squidgy parts.

Fellow forum members have already made great suggestions specifically about using apt and the way package management works in Ubuntu/Linux.

> **likewise2 said:**
> I am new to Linux and new to Ubuntu as well. I am presently a windows user who is trying to migrate to linux.

For a more general introduction into the Ubuntu-sphere, please have a look at the link in my sig: "Linux is Not Windows" & "Resources for Newcomers".

The following is also a great user-friendly site for newbies: [https://linuxjourney.com](https://linuxjourney.com)

---

### Post by likewise2 on 2019-04-14
[FONT=&amp]Say, if I am trying to install LAMP. Then all I have to do is to 'apt install httpd', 'apt install mysql' or 'mariadb', 'apt install php'. And apt which is the package manager here will take care of all the dependencies.[/FONT]

[FONT=&amp]Okay so 'apt' my package manager will take care of all the related dependencies, right?[/FONT]

---

### Post by yancek on 2019-04-14
That's one way although a simpler way is to use tasksel.  Both methods are explained at the site linked below.

[https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/](https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/)

---

### Post by 1clue on 2019-04-14
**sudo apt update && sudo apt install apache2 mysql php** would technically do it, but there's more to it than that: [https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04)

The Ubuntu package manager is actually dpkg. Apt is a tool designed to make dpkg less cryptic. You could also use the Synaptic gui tool, or others. 

As a general rule of thumb, don't ever try to hunt down dependencies. Over time, the dependencies on applications change. If you have deliberately installed something which is only a dependency of the thing you really want, the system will keep it around even when it's no longer needed. Install only the apps you actually want.

There are several types of packages installed on your system:

[LIST=1]
[*]Things included in the base system, when you installed Ubuntu in the first place. 
[*]Things you installed by name. 
[*]Dependencies. 
[*]One-time apps needed only during an install, and then not needed anymore after that. 
[/LIST]

The package manager keeps track of which things are installed by each method. If you run housekeeping commands the package manager will clean out/remove things which are in slots 3 or 4.

In other words, trust the package manager and keep your list of "installed" packages small.

Managing dependencies is much more complicated than just having the latest version of some library. Different apps on your system may need specific versions of the library, not necessarily all the same one. The package manager takes care of all that.

---

