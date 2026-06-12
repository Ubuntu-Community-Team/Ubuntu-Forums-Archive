---
title: "help with OpenGL setup...."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by NeoEIRE on 2008-05-13
hi, i am trying to run "EVE trinity Online" but its crashing...
on the test menu it says the OpenGL is not setup correctly...

how to i set it up OpenGL on ubuntu 7.04 64bit?????

plus i see some people are able to run games.. HOW? i have battlefireld 1942/2, call of duty 2/3, sim city 4 and none of them run at all...
i have never got one of my games to run, including "Worms Armageddon" which should have no issues...

---

### Post by NeoEIRE on 2008-05-13
any ideas?

---

### Post by pytheas22 on 2008-05-13
OpenGL should be set up correctly by default.  Are you able to enable desktop effects (go to System>Preferences>Appearance and try turning them on)?  If you are, then OpenGL is working.

I'm also not sure how you're trying to run the games you mention, but if you're new to Linux, I suspect that they're Windows games  (i.e. their executables end in .exe) and you're trying to run them directly in Linux.  This won't work at all.  You can, however, install a program named wine that can run many Windows applications, including games, fairly well.

Please let us know if this games are meant for Windows, and if so, whether you're using wine or not.

---

### Post by NeoEIRE on 2008-05-14
the desktop effects work, but the system test for (linus, ubuntu)version of EVE online says that the openGL failed its test.

as for the games, i do have wine, i have had this system for 2 years and not been able to run any windows game... i have been told wine should work but it never does...

is it just 7.04 feisty just doesnt work?

---

### Post by pytheas22 on 2008-05-14
Have you tried following the instructions at [http://support.eve-online.com/Pages/KB/Article.aspx?id=387](http://support.eve-online.com/Pages/KB/Article.aspx?id=387) ?  More information is at [http://support.eve-online.com/Pages/KB/Browse.aspx?categoryID=92&language=EN](http://support.eve-online.com/Pages/KB/Browse.aspx?categoryID=92&language=EN) ... there are some links about various video cards, compiz and so on.  You should read through it; maybe it will solve your problem.

Upgrading to a newer version of Ubuntu also might not hurt.  It could be that the OpenGL package for 7.04 is too old.  The eve documentation says that the game should work with 7.04 and up, but you never know.

As for Windows games and wine, you should take a look at the database, [http://appdb.winehq.org/](http://appdb.winehq.org/) .  It provides information on how well programs work under wine and any special tweaking required.  The steps to get Sim City 4 running almost flawlessly, for instance, are at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7500&iTestingId=17935](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7500&iTestingId=17935) .

---

### Post by Perfect Storm on 2008-05-14
AFAIK, eve-online for linux works mostly for nvidia-cards (using cedega wrapper), so if you don't have nvidia card you'll properly be without luck.

---

