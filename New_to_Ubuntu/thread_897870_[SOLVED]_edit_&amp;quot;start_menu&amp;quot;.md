---
title: "[SOLVED] edit &amp;quot;start menu&amp;quot;"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by xusword on 2008-08-22
Hi:

About the "start menu" (The pull down menu that is labeled "Applications" on the top left by default)

How do I configure it?

1. I would like to know what command each menu item executes. I would like to be able to update the system when I am using the non-administrative account and su to it in command line.

2. I wonder where each item gets it icon from. I would need to know the location of the image when I try to configure a QuickLuncher.

3. It would also be nice to know how to add/remove menu items there as well.

thanks

---

### Post by t0p on 2008-08-22
Right-click on the panel where the menu comes out (where it says Applications) and you get an option to edit the menus.

---

### Post by ugm6hr on 2008-08-22
System-> Preferences-> Main Menu

This will allow to activate and inactivate different entries etc, as well as find out what command they run (right-click Properties).

Ooops... Just noticed this is about Xubuntu, not Ubuntu.  XFCE's menu is much less easily modifiable.

---

### Post by unutbu on 2008-08-22
Hello xusword, welcome to the forums.
> 
1. I would like to know what command each menu item executes.

An indirect method might be to click the menu item and then type in a terminal
```
ps axuw
```
One of the last entrees may be the process spawned by the menu item click.

> 
 I would like to be able to update the system when I am using the non-administrative account and su to it in command line.

In Ubuntu, the normal way to gain root powers is to use sudo, rather than su.
For example
```

sudo apt-get update
sudo apt-get upgrade

```

to upgrade packages to the latest versions.

Use gksu for graphical applications:
```

gksu synaptic

```

If you use sudo instead of gksu with some graphical apps, the environment variables are not set right and root may make itself the owner of the normal user's .Xauthority, causing problems.

To get a root shell type
```

sudo -i

```

> 
2. I wonder where each item gets it icon from. I would need to know the location of the image when I try to configure a QuickLuncher.

In Ubuntu, the icons in general are located in /usr/share/icons/. Maybe it is the same for Xubuntu?

> 
3. It would also be nice to know how to add/remove menu items there as well.

I don't have Xubuntu, but perhaps one of these posts will help:

[http://ubuntuforums.org/showthread.php?t=418814](http://ubuntuforums.org/showthread.php?t=418814)
You might be able to edit it this way: [http://ubuntuforums.org/showpost.php?p=5572085&postcount=14](http://ubuntuforums.org/showpost.php?p=5572085&postcount=14)
The location of menu configuration files seems to be ~/.local/share/applications: [http://ubuntuforums.org/showpost.php?p=5571430&postcount=12](http://ubuntuforums.org/showpost.php?p=5571430&postcount=12)
To delete menu items [http://ubuntuforums.org/showpost.php?p=5573477&postcount=16](http://ubuntuforums.org/showpost.php?p=5573477&postcount=16)

---

### Post by xusword on 2008-08-22
Thanks for all your reply

I have having trouble tagging this post "solved" cause I realize the more apporiate place to post such quesiton is in a xfce forum. (and also how do i use the "thank" feature)

---

### Post by cardinals_fan on 2008-08-22
> **xusword said:**
> Thanks for all your reply

I have having trouble tagging this post "solved" cause I realize the more apporiate place to post such quesiton is in a xfce forum. (and also how do i use the "thank" feature)
1. Scroll to the top of the thread and click "Thread Tools" -> "Mark Thread as Solved".  See my pic.

2. To thank someone, click the little gold star at the bottom of their post.  Again, see the pic.

3. You might be interested in [this]("http://wiki.xfce.org/faq#menu") on the Xfce Wiki.

---

