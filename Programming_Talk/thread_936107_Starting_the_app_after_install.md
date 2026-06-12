---
title: "Starting the app after install"
date: 2008-10-02
forum: Programming Talk
---

### Post by DenKain on 2008-10-02
I am sorry if this has already been answered in a previous post but if it has I was unable to find that post. Also, I am sorry if this is a simple answer but this is my first time witting an application for Linux.

I was wondering; after I build my deb package (I am just going to use Debian Package Maker [http://code.google.com/p/debianpackagemaker/](http://code.google.com/p/debianpackagemaker/)) and install it on my system....how do I set it up so that when I type the name of the application in the terminal it will just start running like for example nmap or ufw?

-DenKain

---

### Post by Mindzai on 2008-10-02
I dont know how the package maker works, but to run a program from the command line it needs to be installed in your path somewhere - you can find out which locations are included in your path by typing **echo $PATH** in the terminal.

---

### Post by DenKain on 2008-10-02
Thank you very much. I set the Debian Package Maker to place the program in /usr/local/sbin and it worked the way I wanted it to.

:D

---

