---
title: "[SOLVED] Plasmoid installation woes"
date: 2008-05-24
forum: Programming Talk
---

### Post by wkdude18 on 2008-05-24
I am trying to install the plasmoid pretty task manager from kde-look.org and have followed the instructions from the website and thread posting at "http://ubuntuforums.org/showthread.php?p=4477427", however when I issue make command the following error appears:

make
[ 16%] Building CXX object CMakeFiles/plasma_applet_pretty_tasks.dir/plasma_applet_pretty_tasks_automoc.o
In file included from /home/william/tarball/prettytasks/prettyicon.h:4,
                 from /home/william/tarball/prettytasks/moc_prettyicon.cpp:10,
                 from /home/william/tarball/prettytasks/plasma_applet_pretty_tasks_automoc.cpp:2:
/home/william/tarball/prettytasks/prettytasks.h:19:37: error: taskmanager/taskmanager.h: No such file or directory
In file included from /home/william/tarball/prettytasks/prettyicon.h:4,
                 from /home/william/tarball/prettytasks/moc_prettyicon.cpp:10,
                 from /home/william/tarball/prettytasks/plasma_applet_pretty_tasks_automoc.cpp:2:
/home/william/tarball/prettytasks/prettytasks.h:24: error: ‘TaskManager’ has not been declared
/home/william/tarball/prettytasks/prettytasks.h:25: error: ‘TaskManager’ has not been declared
/home/william/tarball/prettytasks/prettytasks.h:42: error: ‘TaskPtr’ has not been declared
/home/william/tarball/prettytasks/prettytasks.h:43: error: ‘TaskPtr’ has not been declared
In file included from /home/william/tarball/prettytasks/moc_prettyicon.cpp:10,
                 from /home/william/tarball/prettytasks/plasma_applet_pretty_tasks_automoc.cpp:2:
/home/william/tarball/prettytasks/prettyicon.h:22: error: ‘TaskManager’ has not been declared
/home/william/tarball/prettytasks/prettyicon.h:23: error: ‘TaskManager’ has not been declared
/home/william/tarball/prettytasks/prettyicon.h:29: error: expected `)' before ‘task’
/home/william/tarball/prettytasks/prettyicon.h:47: warning: non-static const member ‘PrettyIcon::Private* const PrettyIcon::d’ in class without a constructor
make[2]: *** [CMakeFiles/plasma_applet_pretty_tasks.dir/plasma_applet_pretty_tasks_automoc.o] Error 1
make[1]: *** [CMakeFiles/plasma_applet_pretty_tasks.dir/all] Error 2
make: *** [all] Error 2

Any helpful advice?

---

### Post by LaRoza on 2008-05-24
Do you have all the tools and libraries installed?

---

### Post by wkdude18 on 2008-05-25
Well, I'm not sure which ones specifically you are talking about, but I have kdelibs5-dev,libplasma-dev, cmake(duh), and libphonan-dev (or something like that). Is there one that I'm missing?

---

### Post by wkdude18 on 2008-05-25
Sorry, I'm wrong. after apt-file search taskmanager.h, I found package kde-workspace-dev, installed, and make and make install worked, and now I have a new widget on my desktop.

---

### Post by FrostBlue on 2008-08-28
Could you please upload the default plasmoid which comes with kde 4.1.I tried to install this one and don't have a backup.

Thanks a lot.

---

