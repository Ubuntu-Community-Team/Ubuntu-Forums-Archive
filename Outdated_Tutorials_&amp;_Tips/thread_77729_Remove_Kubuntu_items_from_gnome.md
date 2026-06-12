---
title: "Remove Kubuntu items from gnome"
date: 2005-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by A-star on 2005-10-17
I found this in another thread and it might be usefull to some people:

It removes every kubuntu program from the gnome menu:
```

cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*

```

---

### Post by hanzj on 2005-10-18
Why would you want to remove kubuntu apps?

---

### Post by zipmegabyte on 2005-10-20
Because they clutter Gnome menus and most of them have their Gtk2 counterparts already. (I'd recommend leaving K3B and Amarok though ;) )

Thanks for the tip!

---

### Post by geearf on 2005-11-06
Hello,
would you also know how to do the opposite ? removing gnome apps from kde menu (but I hope they will stay in the debian menu).

thanks

---

### Post by A-star on 2005-11-07
[QUOTE=geearf]Hello,
would you also know how to do the opposite ? removing gnome apps from kde menu (but I hope they will stay in the debian menu).

thanks[/QUOTE]
I have no clue, but I think someone else will be able to answer your question.

---

### Post by geearf on 2005-11-07
thanks anyway :)

---

### Post by Paool on 2005-11-08
thanks :D this is what I'm looking for yesterday :D:D

---

### Post by nmastae on 2006-02-21
[QUOTE=geearf]Hello,
would you also know how to do the opposite ? removing gnome apps from kde menu (but I hope they will stay in the debian menu).

thanks[/QUOTE]


Would this work?

[COLOR="Blue"]cd /usr/share/applications/gnome
sudo chmod a+rw /usr/share/applications/gnome/*
for i in *; do echo "OnlyShowIn=gnome;" >> $i; done
sudo chmod 644 /usr/share/applications/gnome/*[/COLOR]

---

### Post by nmastae on 2006-03-14
[QUOTE=A-star]I found this in another thread and it might be usefull to some people:

It removes every kubuntu program from the gnome menu:
```

cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*

```[/QUOTE]
Excellent! This worked perfectly. Thanks, A-Star! :)

---

### Post by gazj on 2006-03-30
[http://www.kde-look.org/content/show.php?content=31031]("http://www.kde-look.org/content/show.php?content=31031")

try this, it doesn't remove the gnome items from your kde menu, but nicely puts them all in a gnome submenu :)

---

### Post by Nordoelum on 2006-04-02
[QUOTE=A-star]I found this in another thread and it might be usefull to some people:

It removes every kubuntu program from the gnome menu:
```

cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*

```[/QUOTE]
Thank you so much :D

---

### Post by Nordoelum on 2006-04-03
Can I use the command:
```
 
$ sudo apt-get remove kubuntu-desktop

```
 
Will this remove everything that came with the command:
```
 
$sudo apt-get install kubuntu-desktop

```
?

---

### Post by Ensnared on 2006-04-05
[QUOTE=Nordoelum]Can I use the command:
```
 
$ sudo apt-get remove kubuntu-desktop

```
 
Will this remove everything that came with the command:
```
 
$sudo apt-get install kubuntu-desktop

```
?[/QUOTE]
No, but there's instructions on how to do that in [this post](http://www.ubuntuforums.org/showthread.php?t=96048).

Basically, the kubuntu-desktop package is only a meta-package, meaning it contains no actual data, only dependencies on the actual packages that make up KDE for Ubuntu. So in order to remove them again, you need to remove each package explicitly. The post I linked above shows the command to do just that :)

---

### Post by Nordoelum on 2006-04-05
[QUOTE=Ensnared]No, but there's instructions on how to do that in [this post](http://www.ubuntuforums.org/showthread.php?t=96048).

Basically, the kubuntu-desktop package is only a meta-package, meaning it contains no actual data, only dependencies on the actual packages that make up KDE for Ubuntu. So in order to remove them again, you need to remove each package explicitly. The post I linked above shows the command to do just that :)[/QUOTE]
Thank you so much :D

---

### Post by Kedster on 2008-01-07
that deb file program for kde well i was wondering if theres is sumthin that does the same thing

---

### Post by Kedster on 2008-01-07
lol
i found one 
[http://www.gnome-look.org/content/show.php/Gnome+Menu+Extended+%28Debian+Package%29?content=31035&PHPSESSID=ba4839721c243c2431018d1518febff6]("http://www.gnome-look.org/content/show.php/Gnome+Menu+Extended+%28Debian+Package%29?content=31035&PHPSESSID=ba4839721c243c2431018d1518febff6")

---

