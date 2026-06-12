---
title: "desktop window manager"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-08-30
I heard that while running xubuntu you could download some file to get the gnome manager, but is there a way to get the kde manager while in ubuntu, and switch from gnome to kde between sessions?

---

### Post by szymon_g on 2008-08-30
hm... you can have 2 (or more) desktop environments/window managers at one system... its  not a problem (but you may have a bit mess with qt and gtk programs- they will work, but, by default, they may look differently)

---

### Post by gmxgeek on 2008-08-30
To switch, there should be an option on the login menu i think. Lower left corner once you get them installed

---

### Post by hyperhopper on 2008-08-30
How can you do this (and what are qt and gtk programs?)

---

### Post by hyperhopper on 2008-08-30
> **gmxgeek said:**
> To switch, there should be an option on the login menu i think. Lower left corner once you get them installed

I at least knew that =]

---

### Post by gmxgeek on 2008-08-30
should be able to get it from the repos

---

### Post by hyperhopper on 2008-08-30
All i am asking for is the name!!!
What is the title of what i must get?

---

### Post by gmxgeek on 2008-08-30
kde :)

search for kde and it is just called kde as far as i know

---

### Post by Lacrimstein on 2008-08-30
```
sudo apt-get install kubuntu-desktop
```

Keep in mind though that this will change your login manager to kdm (I think in hardy it gives you a choice when installing) and your bootsplash to kubuntu logo. This will install all kubuntu versions of application.

You could also probably do the following:
```
sudo apt-get install kde
```

But then you will have to install each application, like amarok, separately.

You can also install KDE 4, but I don't recommend it since its still 4.0 in the repositories and not very stable (for me at least)
```
sudo apt-get install kde4
```

---

### Post by gmxgeek on 2008-08-30
kde4 is uuuuugly

---

### Post by szymon_g on 2008-08-30
> **hyperhopper said:**
> How can you do this (and what are qt and gtk programs?)

you can get it by typing*

sudo aptitude install kdebase

i suggest using kdebase instead of full kubuntu-desktop metapackage- becouse its smaller and more flexible (at least for me ;p) than 'full' kde.
and second part of question...
QT and GTK are two the most important (and popular) graphic libraries- programs use them for creating graphics (i.e- if you run any graphical programs, you have to have at least one of them installed)- QT libraries are used mostly by kde programs (and by kde itself), GTK are used by GNome/xfce programs. both libraries has different default look- but they may look the same (at least under kde- hint: gtk-qt-engine /or was it qt-gtk-engine?/).

*in console/terminal.
you use synaptic, of course

---

### Post by hyperhopper on 2008-08-31
this is all kinda confusing--- from what I know- gnome is my windows manager, and the only difference between ubunu and kbuntu is the manager so installing kde and changing session type should make it as if I were using kde/kbuntu

Am i correct?

---

### Post by hyperhopper on 2008-08-31
And if I am correct, then is there a way to download KDE and run ubuntu but have it as if kubuntu were running?

---

### Post by hyperhopper on 2008-09-01
but If I am indeed correct, which of the methods stated previously must I use to reach the stated goal

---

### Post by hyperhopper on 2008-09-01
bump is anybody out there?

---

### Post by habtool on 2008-09-01
sudo apt-get install kubuntu-desktop

then select kde from option, pulldown menu, at login screen, where you enter username and password on bootup.

(Like previous poster mentioned, having both ubunut-desktop and kubuntu desktop does make things somewhat messy)

But we have all gone down this road when we first started with Ubuntu, so go for it no time like the present to learn.

Have fun

---

### Post by hyperhopper on 2008-09-01
> **Lacrimstein said:**
> ```
sudo apt-get install kubuntu-desktop
```

Keep in mind though that this will change your login manager to kdm (I think in hardy it gives you a choice when installing) and your bootsplash to kubuntu logo. This will install all kubuntu versions of application.

You could also probably do the following:
```
sudo apt-get install kde
```

But then you will have to install each application, like amarok, separately.

You can also install KDE 4, but I don't recommend it since its still 4.0 in the repositories and not very stable (for me at least)
```
sudo apt-get install kde4
```
SO when I do that, I still keep gnome, but get kde as an extra option?

---

### Post by nothingspecial on 2008-09-01
> **hyperhopper said:**
> SO when I do that, I still keep gnome, but get kde as an extra option?

Yes, but it makes stuff messy, even messier than the penguins!

---

### Post by billgoldberg on 2008-09-01
> **hyperhopper said:**
> this is all kinda confusing--- from what I know- gnome is my windows manager, and the only difference between ubunu and kbuntu is the manager so installing kde and changing session type should make it as if I were using kde/kbuntu

Am i correct?

No, Metacity or Compiz Fusion is your windows manager. Gnome is a Desktop Environment.

--

Well Ubuntu and Kubuntu, besides using a Different DE, also have different apps. 

If you install the kde package, you won't be using Kubuntu. You will just be using KDE on Ubuntu.

If you install the package "kubuntu-desktop" then yes, you are using Kubuntu (when you log into your kde session).

---

### Post by hyperhopper on 2008-09-01
If I do this and screw up, can I get back to how I am now?

---

### Post by hyperhopper on 2008-09-01
> **nothingspecial said:**
> Yes, but it makes stuff messy, even messier than the penguins!
love penguin reference...

---

### Post by nothingspecial on 2008-09-02
> **hyperhopper said:**
> If I do this and screw up, can I get back to how I am now?


Yep, have a look at this

[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by hyperhopper on 2008-09-03
this suggests that i use aptitude to install it, how do I do that?

---

### Post by nothingspecial on 2008-09-03
```
sudo aptitde install kubuntu-desktop
```

---

### Post by hyperhopper on 2008-09-03
whats the difference between aptitude ant apt-get?

---

### Post by philinux on 2008-09-03
There used to be but not so much now as apt-get has an autoremove option.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Elfy on 2008-09-03
In this case though if you install kubuntu-desktop it will get all the kde apps, removing with apt-get will remove only the -desktop and leave all the programs behind.

---

