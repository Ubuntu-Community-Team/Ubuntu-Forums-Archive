---
title: "HOW TO: Get *.lists and such the easy way."
date: 2005-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by BLTicklemonster on 2005-12-05
I couldn't think of a better name for this thread, sorry.

Do you get tired of having to go to the terminal and type 

```
sudo gedit /etc/whatever/something.list or whatever
```


when you are having problems with a particularly buggy install, or maybe you want to be able to put your favorite [repository listing](http://www.psychocats.net/linux/sources.php) in sources.list whenever you have something rewrite them?

Have no fear, because I am lazy as all get out, and I'm here to help.

Let's use the grub menu list for example. I was experimenting with getting xp and ubuntu to dual boot, and I kept having to go back to 

```
sudo gedit /boot/grub/menu.lst
```

over and over again. So I decided to heck with this, I'm AUTOMATING MY TASK!! or cheating, one or the other.

Right click on the desktop, and click on create launcher.

At the top, for this particular instance, put Grub Menu List as the name, put whatever you want for the generic name, or pass it up, same with comment, but in the line "Comm_a_nd:" put this

```
sudo gedit /boot/grub/menu.lst
```

click on run in terminal, and click ok.

Now double click the icon, enter your password, press enter, and voila.


Oh, save that link in your favorites!!!

-Think Snow,
Ticklemonster

---

