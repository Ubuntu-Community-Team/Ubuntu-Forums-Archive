---
title: "i want to use emerald to change my window theme"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-17
but cannot figure it out. anyone?

---

### Post by boombox1387 on 2008-09-17
What are you having troubles with?  Installing the program or using it?

---

### Post by Locutus_of_Borg on 2008-09-17
emerald-theme-manager not working?

---

### Post by tuxxy on 2008-09-17
Download emerald from the repos, use syanptic

once downloaded press ALT + F2 and run this command

```
emerald --replace
```

Now emerald is loaded use the theme manager to change themes, also you can add that command to your sessions to prevent you having to run it every bootup

---

### Post by starcannon on 2008-09-17
> **PatrickMoore said:**
> but cannot figure it out. anyone?

```
sudo apt-get install emerald fusion-icon
```

then go to [http://www.gnome-look.org](http://www.gnome-look.org)

Find a nice emerald theme, (look in the compiz and beryl areas)

Download it to a folder, I keep mine at ~/Themes
Open up Emerald {System>Preferences>Emerald Theme Manager}

Click on Import, browse to the directory where you saved the theme from gnome-look.org.

Open up Fusion Icon {Applications>System Tools>Compiz Fusion Icon}

R+click the Fusion Icon that appeared in you system tray (upper right corner of default gnome-panels)
Choose "Select Window Decorator"
Choose "Emerald"
R+click the Fusion Icon again and select "Reload Window Manager"

Enjoy.

---

### Post by PatrickMoore on 2008-09-17
> **starcannon said:**
> ```
sudo apt-get install emerald fusion-icon
```

then go to [http://www.gnome-look.org](http://www.gnome-look.org)

Find a nice emerald theme, (look in the compiz and beryl areas)

Download it to a folder, I keep mine at ~/Themes
Open up Emerald {System>Preferences>Emerald Theme Manager}

Click on Import, browse to the directory where you saved the theme from gnome-look.org.

Open up Fusion Icon {Applications>System Tools>Compiz Fusion Icon}

R+click the Fusion Icon that appeared in you system tray (upper right corner of default gnome-panels)
Choose "Select Window Decorator"
Choose "Emerald"
R+click the Fusion Icon again and select "Reload Window Manager"

Enjoy.

thank you works like a charm

---

