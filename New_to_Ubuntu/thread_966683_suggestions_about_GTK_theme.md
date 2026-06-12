---
title: "suggestions about GTK theme"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-01
hi everyone.please suggest some GTK themes,with a non dark panel and really good looking menu.

---

### Post by stonecoldjha on 2008-11-01
also,is there a KDE/KDE 4 like GTK theme for gnome?

---

### Post by stonecoldjha on 2008-11-01
i would really like to have a GTK theme that looks like KDE.

---

### Post by iKonaK on 2008-11-01
[kde4]("http://kims-area.com/?q=node/63") is grate ;)

---

### Post by stonecoldjha on 2008-11-01
is there any GTK theme with a glassy gnome panel,and glassy menus?

---

### Post by Idefix82 on 2008-11-01
Have you had a look at [http://www.gnome-look.org/]("http://www.gnome-look.org/")? It has the best collection of GTK themes I know of.

---

### Post by stonecoldjha on 2008-11-01
yeah,i know that,in fact i visit it everyday to find if there is a new GTK or beryl theme that i find attractive,though it rarely happens that i like a theme and apply it.but,i want to have a theme which has menus resembling glossy glass,and a glassy gnome panel.can i request for creating such a theme somewhere?also,it should have a green glossy advancer.thanks.

---

### Post by stonecoldjha on 2008-11-01
can someone make this theme?i believe it would look,sleek,beautiful as well as professional.

---

### Post by darkvampire on 2008-11-01
To be really picky about themes, it is really best to make your own. However: If you wish not to learn the required skills then I advise you find the closest possible theme on Gnome Look.

[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by stonecoldjha on 2008-11-01
i would really like to make themes.what are the skills required?will it take much time to learn them.

---

### Post by darkvampire on 2008-11-01
> **stonecoldjha said:**
> i would really like to make themes.what are the skills required?will it take much time to learn them.

I really do not know. I'll do a bit of research for a tutorial for you.
Someone may post with the knowledge in the meantime, however.

---

### Post by darkvampire on 2008-11-01
It seems your going to need to know programing.

**Gnome's GTK Tutorial**
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

**Guide to GTK theme creation**
[http://orford.org/gtk/](http://orford.org/gtk/)

---

### Post by darkvampire on 2008-11-01
> **iKonaK said:**
> [kde4]("http://kims-area.com/?q=node/63") is grate ;)

This looks really well done.

---

### Post by stonecoldjha on 2008-11-02
but,is anyone out there using some glassy GTK theme which has glossy glassy menus and panel?can someone make this theme?

---

### Post by darkvampire on 2008-11-02
If you want something which resembles KDE, why not just use KDE? :wink:

On your current Ubuntu installation (I'm presuming your using ubuntu) open up the terminal and type the command:
> sudo aptitude update && sudo aptitude install kubuntu-desktop

During the installation process, you should be asked whether you want to use KDM or GDM as your default display manager. If you think you'll use KDE more frequently, make KDM your default. If you think you'll use Gnome more frequently, keep GDM as your default.

The default can always be changed later by modifying the /etc/X11/default-display-manager file. For KDM, the file should read /usr/bin/kdm; for GDM, the file should read /usr/sbin/gdm

When KDE is done installing, log out.

Click on Options and then Select Session.

In the Sessions dialogue, select KDE and then Change Session.

Finally, before you log back in again, decide whether you want to change to KDE just for this session or if you want to make KDE your default desktop environment.

Then, log back in, and you should be using KDE.

To switch back to Gnome, just log out and select Gnome from the session menu.

If you later decide you don't want KDE any more, go back to the terminal and paste in:
> sudo aptitude remove kubuntu-desktop

---

### Post by stonecoldjha on 2008-11-02
i do have KDE installed in ubuntu hardy that i use,but i always use gnome,and presently i use KDE oxygen GTK theme.so,the problem of having a KDE like environment is solved.i actually just wanted to know if there is any GTK theme with glassy menu and panel,if someone out there is using such a beautiful theme.i would also request to make such a theme.

---

### Post by darkvampire on 2008-11-02
Are you looking for something like [Vista Aero?]("http://www.gnome-look.org/content/show.php/Aero-clone?content=57352")

It is quite hard to find a half-decent glassy GTK theme. :wink:

---

### Post by stonecoldjha on 2008-11-02
i do not use vista like themes,and it is not glassy.is it?thanks.

---

### Post by darkvampire on 2008-11-02
> **stonecoldjha said:**
> i do not use vista like themes,and it is not glassy.is it?thanks.

Vista Aero is designed to make your desktop look like glass.

**Screenshot**
[http://download.microsoft.com/download/b/7/4/b74099b2-b694-47fc-8f0f-21e3e88c5d2a/Oberfl%C3%A4che%20Glass.png]("http://download.microsoft.com/download/b/7/4/b74099b2-b694-47fc-8f0f-21e3e88c5d2a/Oberfl%C3%A4che%20Glass.png")

Could you not use Compiz or Emerald? There are many glass themes for them. (:

---

### Post by Cycron on 2010-08-22
sorry to bump an old post, but that is not true that you have to know programming, you simply have to change the images in a theme*
*this only works on pixmap themes (themes that use images instead of code)

---

