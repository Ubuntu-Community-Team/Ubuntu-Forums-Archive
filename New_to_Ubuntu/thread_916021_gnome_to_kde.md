---
title: "gnome to kde ?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by eric489 on 2008-09-10
Hi everybody !

As a total ubuntu noob, I refer to your wisdoms once again.

I've got ubuntu gnome 8.04 and just for the lolz, I wanna change the interface to kde.

Is it possible ? Or should i re-install ubuntu again and choose kde instead ?

---

### Post by Idefix82 on 2008-09-10
You can have both GNOME and KDE and choose between them on startup.
Maybe this will help: [http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

---

### Post by Sycron on 2008-09-10
I like GNOME.

---

### Post by natman on 2008-09-10
There is no need to reinstall, just open up synaptic and search for KDE and select KDE3.5.9 base and any other you want. ( KDE 4 is not final yet )
Note when you boot up before you log in you now will have the option ( under session ) to select either Gnome or KDE )
Also when shuting down from KDE it may return you to log in screen the reason is KDM and GDM. At the moment your using the gnome display manager, when you take KDE you will need the KDM ( KDE desktop manager ) also found in synaptic.
Happy desktopping!

---

### Post by ooobuntooo on 2008-09-10
Install Kubuntu!

[http://www.kubuntu.org/](http://www.kubuntu.org/)

---

### Post by t0p on 2008-09-10
If you want to try KDE, type this into a terminal:

```
sudo apt-get install kubuntu-desktop
```

**Kubuntu-desktop** is a "meta-package" - when you install it, you'll also install a load of applications etc that come with kubuntu.

You will then have both gnome and KDE on your computer.  Whenever you log in, you will be able to choose which desktop environment to use by clicking on the Sessions tab on the login screen.

---

### Post by acidsolution on 2008-09-10
well i like gnome but u can install Kde along with gnome desktop

```
 sudo apt-get install kubuntu-desktop 
```

---

### Post by eric489 on 2008-09-10
> **acidsolution said:**
> well i like gnome but u can install Kde along with gnome desktop

```
 sudo apt-get install kubuntu-desktop 
```

When typing the command in the terminal i get this :

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? ```
E: Får ikke låst /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by acidsolution on 2008-09-10
is your package manager working ???
have u opened synaptic package manager ???
if yes than close it ..
and than try

---

### Post by Oldsoldier2003 on 2008-09-10
> **eric489 said:**
> When typing the command in the terminal i get this :

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? ```
E: Får ikke låst /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

make sure you dont have synaptic, add/remove, or the updater open.

---

### Post by eric489 on 2008-09-10
Sorry, synaptic was open :X

---

### Post by eric489 on 2008-09-10
thanks i finally got it !

---

### Post by Sycron on 2008-09-11
ehh, it wasn't so hard.

---

### Post by alexkrivosh on 2008-09-11
KDE? Gnome? Fluxbox!

---

### Post by Sycron on 2008-09-12
Openbox and slim login manager...

---

