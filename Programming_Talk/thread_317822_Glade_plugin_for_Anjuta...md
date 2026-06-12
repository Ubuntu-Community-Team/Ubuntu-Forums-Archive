---
title: "Glade plugin for Anjuta?.."
date: 2006-12-13
forum: Programming Talk
---

### Post by Jefim on 2006-12-13
Hi, I'm very new to gnome programming and recently I started studying glade and anjuta. Everything worked right until I understood, that the glade plugin for anjuta is not enabled (it is shown in anjuta only when "only show activatable plugins" checkbox is UNchecked). Well, I know, that I can just use glade and anjuta separately, but, really, what is the problem with this plugin? I use Anjuta 2.0.2 and Glade version is 2.12.1 (from Ubuntu Edgy repos). Can anyone point to the cause of this strangeness?

---

### Post by squirrelix on 2007-02-24
Hey, I am having the same problem. Did you ever find any resolution to this? I am using Anjuta 2.1.1.

When I look at the widget properties window in Anjuta, it is a different properties window than when I start glade (from a command line) by itself. Why is this? 

As Jefim noted, there is a glade plugin that is unchecked and I can't seem to check it. 
 
Any ideas anyone?
Thanks

Squirrelix

---

### Post by shrimphead on 2007-02-24
Might have something to do ith the version of Anjuta in the edgy repos being alpha software?

---

### Post by duff on 2007-02-24
I think that plugin requires glade-3

---

### Post by eduardomartin71 on 2008-01-07
There is a bug with anjuta, It seems that some of the function calls have changed between versions of glade ([https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/126314](https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/126314))  they provide a patch but i do not know how to apply it. help needed!!!!

thanks in advanced

---

### Post by kh_naba on 2008-02-05
Just open the glade file (either from the file manager or open dialog). You should get glade started inside anjuta.

---

### Post by 80aless on 2010-01-07
and where do I find a glade file to start Glade? I m starting from scratch following this tutorial: 
[http://www.micahcarrick.com/04-20-2005/gnome-anjuta-programming-tutorial.html](http://www.micahcarrick.com/04-20-2005/gnome-anjuta-programming-tutorial.html)
He says "We will now create our basic GUI. You can either select 'Edit Application GUI' from the 'Project' file menu in Anjuta or press ALT+G to launch Glade"

Edit: Ok I think I made it. Launch glade from Programming > Glade, make something and save the file. then open it from Anjuta as kh_naba said

---

