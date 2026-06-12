---
title: "copy or move and paste duplicates renaming them with gui"
date: 2014-11-07
forum: New to Ubuntu
---

### Post by siretfel2 on 2014-11-07
hi all,
is there a program in ubuntu to copy or move files from one folder to another and rename them when paste?
sometimes i copy or move files from one folder to another (2-5 file maybe) and when paste i want to rename if there's a duplicate automatically. Terracopy for example in windows offers this option. Is there a plugin in thunar or nautilus?

---

### Post by ibjsb4 on 2014-11-07
I do not use it, but got some hits here that may help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Teracopy&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Teracopy&sa=Search&cof=FORID:9)

---

### Post by nerdtron on 2014-11-07
sudo apt-get install ultracopier

When it is active, it will capture your copy/move operations. It also has a default rename (which you can change) on its settings.

---

### Post by lestcape on 2014-11-27
_[SIZE=5]**Helps you to integrate UltraCopier on the Nautilus/Nemo file browser.**[/SIZE]_

**After install (**please select one option**):**

[LIST]
[*]Restart your computer(recommended)
[*]Logout and login
[*]Execute for:
[LIST]
[*]      *Nemo:* nemo -q (save your work first)
[*]      *Nautilus:* nautilus -q (save your work first)
[/LIST]
[/LIST]

**To configure your keyboard shortcut**:
Rigth click on the desktop and then in Configure UltraCopier.

**To install on ubuntu 14.04:**

[LIST]
[*]For Nemo:
[/LIST]
```

sudo add-apt-repository ppa:lestcape/ultracopier-extensions
sudo apt-get update
sudo apt-get install nemo-ultracopier

```

[LIST]
[*]For Nautilus:
[/LIST]
```

sudo add-apt-repository ppa:lestcape/ultracopier-extensions
sudo apt-get update
sudo apt-get install nautilus-ultracopier

```

**To remove:**

[LIST]
[*]For Nemo:
[/LIST]
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:lestcape/ultracopier-extension
sudo apt-get purge nemo-ultracopier

```
[LIST]
[*]For Nautilus:
[/LIST]
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:lestcape/ultracopier-extension
sudo apt-get purge nautilus-ultracopier

```

**Report any problem:**
For Nautilus: [https://github.com/lestcape/Nautilus-UltraCopier-Extension](https://github.com/lestcape/Nautilus-UltraCopier-Extension)
For Nemo: [https://github.com/lestcape/Nemo-UltraCopier-Extension](https://github.com/lestcape/Nemo-UltraCopier-Extension)

---

