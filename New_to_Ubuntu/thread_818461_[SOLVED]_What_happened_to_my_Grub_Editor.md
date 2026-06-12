---
title: "[SOLVED] What happened to my Grub Editor?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by stevezygote on 2008-06-04
I bit the bullet. I installed (K)Ubuntu. So pretty. So stable. But I'm still learning. It isn't in a Wu bi installation any more. It's now in a partition of its own. 

But the thing is I have TWO entries in my Grub for the operating system, and then down below one for Windows XP Home SP3. I'd like to edit my grub to clean it up and to make Windows my default, since I'm still quite unfamiliar with Ubuntu, although very impressed! 

I downloaded KGrubEditor from a repository and installed it using Adept Manager. But do you think I can find it now? It doesn't seem to have gone to any menu item. Can someone please help? Thanks!

---

### Post by drs305 on 2008-06-04
I just wrote this today - good timing I guess ;-)

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

I didn't explictly say how to make windows the default in that post.

You should be able do it from StartUp-Manager and that would be the easiest place to do it. Go to System, Admin, StartUp-Manager and see if you can select Windows as the default operating system. 

If you can't do it through StartUp-Manager, you can do it by editing the menu.lst *default* option. Count the number of kernel entries, then windows. The first kernel is 0, the second is 1, etc. Windows would normally be the third operating system, so the line would be *default 2*. If you aren't sure, post your /boot/grub/menu.lst here and we can tell you.

---

### Post by sayakb on 2008-06-04
```
gksudo kate /boot/grub/menu.lst
```And comment the lines (add a #) rather than removing them.

---

