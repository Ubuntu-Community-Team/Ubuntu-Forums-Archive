---
title: "How to: remove Kubuntu items in the Gnome menu"
date: 2005-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by A-star on 2005-08-24
I found this in another thread and it might be usefull to some people:

It removes every kubuntu program from the gnome menu:
```

cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*

```

---

### Post by Knome_fan on 2005-08-24
You can scrap the chmod part if you do it as root, that is use sudo -s first.

---

### Post by theine on 2005-10-07
Or alternatively...
```

for i in /usr/share/applications/kde/*; do echo "OnlyShowIn=KDE;" | sudo tee -a $i; done

```

---

### Post by lizardo on 2005-10-08
Or still:

```
sudo sed -i '/OnlyShowIn=/d;$a\OnlyShowIn=KDE;' \
    /usr/share/applications/kde/*.desktop
```

which will also remove any existing "OnlyShowIn" settings before adding "OnlyShowIn=KDE;".

---

### Post by ChaKy on 2005-10-09
[QUOTE=lizardo]Or still:

```
sudo sed -i '/OnlyShowIn=/d;$a\OnlyShowIn=KDE;' \
    /usr/share/applications/kde/*.desktop
```

which will also remove any existing "OnlyShowIn" settings before adding "OnlyShowIn=KDE;".[/QUOTE]

How do I now remove OnlyShowIn=KDE from all *.desktop files? Thanks.

---

### Post by N17R0 on 2005-10-10
Nice, this is what I was looking for, this should become standard in linux.
Who wants to see KDE items in GNOME or XFCE anyway, if u want to 
run KDE-apps then login to KDE, thats what Desktop environments are for right?

[Problem]
I have XFCE+GNOME+KDE on my Ubuntu installed, now what hack can I use,
so I have it like this when I login to one of these desktop environments:
KDE = only the KDE apps visible in the kde menu
GNOME = only the GNOME apps visible in the gnome menu
XFCE = only the XFCE apps visible in the xfce menu
[XFCE = only the xfce+gnome apps visible in the xfce menu]
[XFCE = only the xfce+kde apps visible in the xfce menu]

So I don't have to browse 10 miles of menu entry's to find the app I want to use.

TIA

---

### Post by Orunitia on 2005-10-17
You should add this to the Breezy forum, so more people will see this. It's nice to not have KDE programs in my menu that I never use in gnome.

---

### Post by A-star on 2005-10-17
will do that now.

---

### Post by Adrian on 2005-11-08
Just thought I'd link to two recent discussions on this subject. Maybe someone will find them useful.

[http://www.ubuntuforums.org/showthread.php?t=70410](http://www.ubuntuforums.org/showthread.php?t=70410)
[http://www.ubuntuforums.org/showthread.php?t=70679](http://www.ubuntuforums.org/showthread.php?t=70679)

---

### Post by rlgoddard on 2006-06-22
[quote=A-star]I found this in another thread and it might be usefull to some people:

It removes every kubuntu program from the gnome menu:
```

cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*

```[/quote] 
This is an old thread, but I have the same problem as in Breezy.  I have Dapper Drake.  Would this work in Dapper as well?  Do I need to modify any commands to make it work in Dapper?

Take care,
Russ

---

### Post by Zelut on 2007-07-17
Thanks for the tips here guys.  I wrote this up as a tutorial on my blog and also wrote a shell script to do all the dirty work.  If you're interested you can check out both below.  (tested on Feisty, for gnome and KDE.  No Xfce support yet).

[menu-cleaner]("http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/")

---

### Post by VitaminBB on 2008-11-08
Im having the same problem right now.

I installed KDE desktop to see how I liked it and now my menu is cluttered with KDE apps.

[B]
How do I hide them when im logged in gnome?[/B]

This seems like such a stupid problem, why would I want KDE apps showing in Gnome,especially if I installed the KDE desktop to use in seperate sessions?

Anyhow, the terminal codes given earlier in this thread didnt work for me and im still stuck with a ton of KDE apps in my Gnome menu.

**Help?**

---

### Post by VitaminBB on 2008-11-09
Anyone ?

---

