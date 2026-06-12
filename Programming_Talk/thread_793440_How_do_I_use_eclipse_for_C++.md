---
title: "How do I use eclipse for C++?"
date: 2008-05-13
forum: Programming Talk
---

### Post by Silpheed2K on 2008-05-13
I downloaded the C++ package from the eclipse website but I have no idea how to install it [i just installed Linux 3 days ago so i'm going to need help learning this whole OS of course]
so.. how do i install the linux eclipse C++ package I downloaded.. it isnt an SH files just a .tar.gz
[http://mirrors.cat.pdx.edu/eclipse/technology/epp/downloads/release/europa/winter/eclipse-cpp-europa-winter-linux-gtk.tar.gz](http://mirrors.cat.pdx.edu/eclipse/technology/epp/downloads/release/europa/winter/eclipse-cpp-europa-winter-linux-gtk.tar.gz)

[www.eclipse.org](www.eclipse.org)

thanks to whoever helps

edit: Also I have the Intel Compiler Suite for Linux that i'd like to use with it (the C++ compilers that is) just so i dont leave anything out

---

### Post by sowelie on 2008-05-13
Create a folder in your home directory and extract the tar.gz file there.  It's in binary form so you don't have to install it.  You just run it from wherever you extract it.  After that, you should be good to go.

EDIT: To clarify, there will be a file inside of the eclipse folder that is extracted called eclipse.  Just run that file, if you want to create a launcher just point it at that eclipse file.

---

### Post by Silpheed2K on 2008-05-13
Thanks.. i previously ran the Add/Remove options in theApplications menu before and it install it... but I uninstalled it cause I didnt want all those java stuff so I was wondering if I had to install this one.

---

### Post by sowelie on 2008-05-13
Yeah, the one in the repos is old anyway.  Always go with the one off of the eclipse sites.  Java is pretty sweet though :-D.

---

### Post by AZzKikR on 2008-05-14
I happen to use the CDT plugin too (C/C++ Developer Tools) for Eclipse. How I installed it was as follows:

[LIST=1]
[*]Download Eclipse. I did not use the repositories from Ubuntu by the way.
[*]I untarred it in /usr/share/eclipse (using sudo, since we're going to /usr/share/).
[*]I started up `**sudo /usr/share/eclipse/eclipse**`. Why sudo? Because the ownerships in /usr/share/eclipse are automatically set to root after untarring.
[*]Through Eclipse's update manager, I installed the CDT. Because it was launched with sudo, it can download the CDT plugin to /usr/share/eclipse/*.
[/LIST]

Do these steps sound familiar? Post any questions, I'll be glad to be of help.

---

### Post by Silpheed2K on 2008-05-15
that's cool.. I appreciate the help.. mine came with the CDT itnegrated I think cause when I went to upgrade it to the CDT it didnt show up and the IBM site said the newer version are already updated with it.

My question is how do i get it to use the intel compilers i have? because i got it set up and it's still using the gcc compilers. I would really like it on the Intel ones just to make sure my code can compile from my other projects. (i use the intel compiler on windows too.. i love my linux though)

edit: nevermind i got eclipse to see the intel compilers finally.. what you do is you merge the folder in /opt/intel/cc/10.1.015/eclipse_support/cdt4.0/eclipse
over the eclipse main directory and then eclipse will be all setup.. thanks for the help.

---

