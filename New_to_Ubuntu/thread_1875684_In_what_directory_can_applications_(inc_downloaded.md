---
title: "In what directory can applications (inc downloaded) be found on Ubuntu 11,10"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by taylor77 on 2011-11-05
How do i get the downloaded applications to actually run in ubuntu 11.10.  We have downloaded software from the the Ubuntu Software Centre but are then unable to locate them anywhere on Ubuntu (including the file system). The Ubuntu Software Centre only gives options for information or removal of the application, not to lauch it as required. Any help would be appreciated. Many Thanks :)

---

### Post by alco75 on 2011-11-05
I'm not sure about the Ubuntu Software Centre, but if you use Synaptic, you can find out where the installed files are by finding the package, going to its properties, and going to the 'Installed Files' tab. In Oneiric, Synaptic isn't available by default so you have to install it first:

```
sudo apt-get install synaptic
```

---

### Post by Bodsda on 2011-11-05
Hi, 

Welcome to the forums.

What app in particular are you having problems with?
You should be able to search for it through unity.

Thanks,
Bodsda

---

### Post by Paqman on 2011-11-05
You don't need to know the location of the file to launch it on Linux. You can launch applications a number of ways:
[LIST]
[*]Hit the Ubuntu symbol at the top of the dock and start typing the name
[*]Hit your Windows key and do the same
[*]Hit Alt-F2 and type the name of the package
[*]Once you've opened it, right click on the icon on the dock and select "keep in launcher" and from then on just click on the icon to launch
[*]Open a terminal and type the name of the package and hit enter
[/LIST]

Or you can also install launchers like Synapse or Gnome-Do or docks like AWN or Docky. Up to you really!

---

### Post by 3rdalbum on 2011-11-05
As you install a graphical program, Ubuntu Software Center asks you if you want to add it to the Launcher. Even if you click "Not Now", the program will become available through the Dash (the big Ubuntu button on the top of the Launcher, then click More Apps).

If it's not added to the Apps view of the Dash, or if you don't get asked if you want to add it to the Launcher, then it's a command-line program. You don't need to locate a command-line program, just type its name in the terminal.

Your question is commonly asked when new users install the 7zip package. They think it's an archive manager of its own right, like on Windows, whereas in fact it's just a command-line utility that the regular Ubuntu archive manager outsources its 7z capabilities to. If you're specifically asking about the 7zip package, just double-click on your ".7z" archive and it will open in the Archive Manager.

---

