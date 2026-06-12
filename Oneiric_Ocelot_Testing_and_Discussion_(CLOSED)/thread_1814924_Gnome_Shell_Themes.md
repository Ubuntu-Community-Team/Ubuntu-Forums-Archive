---
title: "Gnome Shell Themes"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Rifester on 2011-07-30
I need some help installing Gnome Shell themes in 11.10.  I am not sure what the best way is to accomplish this.   The Gnome Tweak tool theme selector does not let me enable it.   I also cannot run Nautilus as root (for some reason) and cannot move my downloaded themes into the Gnome Shell directory.   How are you fine folks changing the shell theme in 11.10?

---

### Post by hakermania on 2011-07-30
I have no idea but to run nautilus with su permissions:
```

gksudo nautilus

```
[DANGEROUS]

---

### Post by Rifester on 2011-07-30
gksudo nautilus is broken for me in 11.10

---

### Post by Harry33 on 2011-07-30
> **Rifester said:**
> gksudo nautilus is broken for me in 11.10

This works well here.

```
gksu nautilus
```

---

### Post by 23dornot23d on 2011-07-30
> 
I need some help installing Gnome Shell themes in 11.10.  I am not sure  what the best way is to accomplish this.   The Gnome Tweak tool theme  selector does not let me enable it.   I also cannot run Nautilus as root  (for some reason) and cannot move my downloaded themes into the Gnome  Shell directory.   How are you fine folks changing the shell theme in  11.10?
Can you show me a screenshot of your Gnome-Tweak-Tool on the setting to change themes ....
and what choices are there ....

Heres mine as an example .... [[COLOR=SlateGray]_***SCREENSHOT***_[/COLOR]]("http://img714.imageshack.us/img714/373/screenshotat20110730185.jpg")

and the themes to select locally should reside in

(your home)/.themes/

hope this helps ..

I must admit though .... this does [COLOR=Red]**not**[/COLOR] now seem to be retaining the theme ..... it changes
and then when you use the overview mode and come back again  It then reverts back to 
the global theme .... also local themes are no longer being displayed in
the overview window ,,,,,

---

### Post by Rifester on 2011-07-30
Here is a screenshot...   How do I enable the shell theme selector like yours?

---

### Post by 23dornot23d on 2011-07-30
Check in you extensions folder ......  extension  user themes is needed ....

(home)/.local/share/gnome-shell/extensions/( gnome-shell-extensions- user themes )

if not there it can be added from one of two places that I know of

1 ..... the [ricotz testing ppa]("https://launchpad.net/%7Ericotz/+archive/testing") ( just enable for [COLOR=Red]loading in the package you need then - disable it[/COLOR] )

or

2 ..... the gnatty pack of extensions .... for the majority of other extensions .....
[Direct download gNatty Pack (Contains themes & extensions) or just the gNatty Extensions]("http://cid-32ec6e89f4aa803b.office.live.com/self.aspx/Linux/gNatty%20Pack.tar.gz") [COLOR=Red]*[/COLOR] Updated 29 June 2011

again download it and look in the file for the things you need ..... and put in the directory .... CBowman did include
a readme too with this ...... ensure metadata.js files match your Gnome-Shell version too ..... should be 3.1.3
( also be aware things move fast and check yourself for later updates )

(home)/.local/share/gnome-shell/extensions/

I am reasonably sure once this is added and you restart Gnome-Shell then that will become active


[URL="http://img10.imageshack.us/img10/5886/screenshotat20110730201.jpg"][COLOR=Blue][U][I][B]Screenshot of mine gnome-shell-extensions user theme
[/B][/I][/U][/COLOR][/URL]

---

### Post by Rifester on 2011-07-30
Thanks!   Got it from the Ricotz ppa, all is well in Gnome shell land!

---

### Post by 23dornot23d on 2011-07-30
Good to hear ..... another success ... ;)

---

