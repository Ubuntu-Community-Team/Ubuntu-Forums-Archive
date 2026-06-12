---
title: "[SOLVED] Creating a mythtv plugin"
date: 2008-03-03
forum: Programming Talk
---

### Post by BillDozer on 2008-03-03
Hi,

I want to try and create a mythtv plugin. And wanted to use the MythHello example from mythtv.org. [http://www.mythtv.org/wiki/index.php/Building_Plugins:HelloMyth]("http://www.mythtv.org/wiki/index.php/Building_Plugins:HelloMyth")

But I have problems compiling it. The compiler cannot find the include files specified.

There probably is some specific Ubuntu set-up that I am not familiair with.

Anyone tried this?

---

### Post by superm1 on 2008-03-07
Hi Bill,

you probably want to make sure you have libmyth-dev installed.  This should pull in all necessary headers.

---

### Post by BillDozer on 2008-03-08
Thanks superm1,

That seemed to do the trick.

I can compile it now without errers.

Let the fun begin...

:-)

---

### Post by sierramike on 2008-04-08
Hello,

I've now managed to compile the mythhello plugiN, and added the lines to mainmenu.xml, also had to move the libmythhello.so to /usr/lib/mythtv/plugins and remove the execute attribute so it is in the directory as the other plugins, and also moved the hello_ui.xml to /usr/share/mythtv/themes/default.

The Myth Hello item is in the root menu of the Frontend, but it does nothing, when I hit 'Enter' on it, nothing happens ...

Can you tell me what it should do ? And also what you did to get it working ?

Note : I'm using Mythbuntu 7.0 ...

Thanks a lot for help ! What type of plugin are you doing ?

---

