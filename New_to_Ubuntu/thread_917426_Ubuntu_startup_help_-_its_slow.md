---
title: "Ubuntu startup help - its slow"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by nexus_2006 on 2008-09-11
I'd like to remove as many things out of my sessions box as I can in order to make 8.04 start up as quickly as possible.  I have "gnome-at-visual -s", and I don't know what it is.  Can I uncheck it?  Also, I don't know if I can uncheck the tracker programs as well.  Any information you guys can give me? 

If you have any other tips to increase my 8.04 boot time I'd appreciate it.

---

### Post by Tatty on 2008-09-11
If you want to analyse boot up times try installing bootchart with this thread:

[http://ubuntuforums.org/showthread.php?t=241604](http://ubuntuforums.org/showthread.php?t=241604)

Then we can see if anything is behaving unessesarily slowly.

---

### Post by nexus_2006 on 2008-09-11
Here we go.  Guess its not too bad.  Still, can I get rid of the visual assistive thing and not notice a difference?  I don't use the magnifier or OSK.  I really was just looking to streamline the process.

---

### Post by cariboo on 2008-09-12
Removing services is not going to help your system boot faster as it is the gui programs that take the longest to load. You could get rid of the gdm and just load a lightweight desktop manager, have a look here:

[http://resources.zdnet.co.uk/articles/tutorials/0,1000002006,39291016,00.htm](http://resources.zdnet.co.uk/articles/tutorials/0,1000002006,39291016,00.htm)

for an article on lightweight Desktop Managers

Jim

---

### Post by nexus_2006 on 2008-09-13
Thanks.  I might look at it.  I used to use fluxbox with Slackware a few years ago and it always loaded super fast.  I kinda decided that since I have a decent graphics card and rarlely play intense graphics games anymore I'd rather keep GNOME with compiz, cairo-dock, etc and just deal with the startup times.  I've been trying suspend and hibernate, they both work really well, much better than I've experienced with other distros and older versions of Ubuntu.  I think I'll setup a lightweight WM that I can switch to when I'm out of the house, something that won't eat battery every time I click a menu or something.  Thanks for the link.

---

