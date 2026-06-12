---
title: "How uninstall softwares included in LUbuntu ?"
date: 2020-07-29
forum: New to Ubuntu
---

### Post by aug7744 on 2020-07-29
Lubuntu install softwares that I not need. How to unnistall Firefox, Libreoffice, bluedevil and some others softwares ? Thanks for reply.

---

### Post by ActionParsnip on 2020-07-29
```

sudo apt-get --purge remove firefox libreoffice bluedevil
sudo apt-get --purge autoremove

```

And so on.

---

### Post by crip720 on 2020-07-29
These should be safe to remove.  Depending on others you want to remove, be careful since some software is tied into the OS and might cause damage(think evolution calendar).  Usually for people you do not want a lot of included software, the min ISO is good so you can add what you want.

---

### Post by aug7744 on 2020-07-30
Thanks for all replies.  "sudo apt-get --purge remove firefox libreoffice bluedevil sudo apt-get --purge autoremove"  Means that Linux not need to use unninstaller how are used in windows ? exactly all files installed will be deleted even configurations ?

---

### Post by Impavidus on 2020-07-30
I don't know about Windows. On Ubuntu, apt (or apt-get, or one of the other interfaces to the same) is the package manager and with the remove action it acts as an uninstaller for all properly packaged software. And you normally avoid software that's not properly packaged. The --purge option means it will also remove configuration. It won't remove user settings though; you have to remove those manually. They should be somewhere in your home directory.

---

### Post by aug7744 on 2020-07-31
-purge
also remove configuration of others softwares ? How that command work ?
How to see the exact name of an software to use in sudo apt-get --purge remove ?

---

### Post by guiverc on 2020-07-31
To see the [reference] manual page for the command `apt-get`, you can use the command

```
man apt-get
```

It will show the following information [http://manpages.ubuntu.com/manpages/focal/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/focal/en/man8/apt-get.8.html)

For finding packages, the following maybe helpful, or you could peruse installed packages (`dpkg -l`), search for packages (`apt-cache search`) or a number of ways. I'll instead provide the following..

The packages included on a Lubuntu desktop ISO, you can view via (for 20.04)

[https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)

You'll note it lists packages in a couple of ways
- depends (these are required)
- recommends

To have a Minimal Lubuntu system, you could install `lubuntu-desktop` with the `--no-install-recommends` option 

By default Ubuntu will install recommended packages; the `--no-install-recommends` will cause these to be skipped, creating a minimal Lubuntu install (for modern Lubuntu 20.04 LTS or an LXQt release, older LXDE releases had alternate ways of achieving this).

Given your system is already installed, the "recommends" packages are also ones you can remove (for a clean system anyway)

Source : [https://discourse.lubuntu.me/t/what-happened-to-the-meta-mackage-lubuntu-core-in-20-04-lts/1045/2?u=guiverc](https://discourse.lubuntu.me/t/what-happened-to-the-meta-mackage-lubuntu-core-in-20-04-lts/1045/2?u=guiverc)

---

### Post by ActionParsnip on 2020-07-31
> **aug7744 said:**
> Thanks for all replies.  "sudo apt-get --purge remove firefox libreoffice bluedevil sudo apt-get --purge autoremove"  Means that Linux not need to use unninstaller how are used in windows ? exactly all files installed will be deleted even configurations ?

Each package is installed with dpkg. This is abstracted with ap(-get) which manages deps for you. Each package can be uninstalled using the dpkg command or apt(-get) command. Each package doesn't need its own uninstaller like in Windows. Each package knows it's contents so when you tell the system to uinstall a package it removes those files and runs any post uninstall sripts.

Please note that uninstalling an application does NOT remove the per-user configuration in each user's $HOME folder. So removing Firefox will not delete the ~/.mozilla/firefox folder. If you uninstall Firefox then reinstall it (as so very many people do) you will still have the old configuration and all you will have done is removed the files that make up Firefox then put the same files back in the same place. Fixes nothing.

If you remove the config files for an application then run them, it will make a vanilla set for you.

---

### Post by Holger_Gehrke on 2020-07-31
As Impavidus said: 'apt remove --purge *packagename*' removes a package and system-wide settings for that package. It won't touch settings you made which are stored in files in your home directory.

There are many ways to find out the package name for a program.

If you know the command to start a program - for example from looking at the EXEC-line in it's .desktop file - you can use the lower, local part of package management what package the program file is part of. You do so with 'dpkg-query -S $(which command)' (example: 'dpkg-query -S $(which firefox)' will print 'firefox: /usr/bin/firefox'; the part before the colon is the package name, the rest of the line is the path and name of the program).

Another way is to use 'apt search' or 'apt-cache search' followed by some word you expect to be in the description of the package. This will often produce lots of output, so sending that output through a pipe into less (a program for viewing and searching text) by adding '| less' to the end of the command is a good idea. 'apt show' followed by a package name will give you all the details about a package.

Like most command line tools apt, apt-get, apt-cache, dpkg, dpkg-query and less are well documented through manual pages which should be available on your computer. To read the manual page use the 'man' command, for example 'man apt'. There is a tool to search for manual pages by keywords named 'apropos', so 'apropos package' will give you a list of manual pages which mention the word 'package' in their first paragraph of text. That too can produce lots of output, so again piping to less might be very helpful.

There are also graphical frontends to package management. There's 'Software' (or gnome-software or "Software Store" or "Snap Store" or whatever Canonical are calling it today) which is aimed at beginners and tries to hide as much of the technical details as humanly possible from the user (which is the reason I neither like nor use it). There's also 'synaptic', which is a lot more technical than "Software" and shows a lot of packages which "Software" doesn't show and offers many options beyond just installing or uninstalling.

Holger

---

### Post by GhX6GZMB on 2020-07-31
For Lubuntu, I strongly recommend that you use the Muon Package Manager (already installed by default).
sudo apt-get purge etc. also works, but you run the risk of losing synchronization between actual installations and the installation database.

I run Lubuntu 20.04 myself, and have found that removal using Muon followed by an apt-get purge command (to get rid of leftover configuration files) works well.

---

### Post by monkeybrain20122 on 2020-08-01
Look, Ubuntu is Linux for humans and that include non geeks, instead of scratching your head over apt-get, apt, purge and all these business that takes a few posts to explain, Lubuntu comes with gui package manager. Search for synaptic, find the application you want to remove, right click and choose remove or completely remove (that is the same as purge) and it will show you what other packages it will remove and so you can decide whether to go ahead or not. If it removes a lot of other stuffs then you'd better keep it because something it removes maybe vital to the system. That's it.
Sorry, it is just nonsense to tell a new user to read man apt-get just to remove some packages.


**Edited**: or muon, which is basically the same as synaptic. Lubuntu used to come with synaptic but maybe the qt version comes with muon, so use that.

---

### Post by aug7744 on 2020-08-02
@crip720
"the min ISO is good so you can add what you want"
I use 3G connection and not has the MODEM driver installed that is the because of my choice to backup all packages.

@ActionParsnip
"Each package is installed with dpkg. This is abstracted with ap(-get) which manages deps for you. Each package can be uninstalled using the dpkg command or apt(-get) command. Each package doesn't need its own uninstaller like in Windows. Each package knows it's contents so when you tell the system to uinstall a package it removes those files and runs any post uninstall sripts."

What ? I use Windows and unhappily has softwares that need to use unninstallers to remove all files. Linux not need unninstallers for any software installed ?

"Please note that uninstalling an application does NOT remove the per-user configuration in each user's $HOME folder."
In Linux any software will allways use $HOME to configuration ? If yes allways is an folder with the name of software ?

---

### Post by TheFu on 2020-08-02
> **aug7744 said:**
>  
"Please note that uninstalling an application does NOT remove the per-user configuration in each user's $HOME folder."
In Linux any software will allways use $HOME to configuration ? If yes allways is an folder with the name of software ?

Packages contain information about all the programs and settings they will use. The package manager understands this and that is who we both install and remove programs.

There are multiple types of settings for most packages:
[LIST]
[*]system-wide settings, usually stored in /etc/ somewhere.
[*]per-userid settings, always stored in $HOME somewhere. Each userid has a different $HOME.
[/LIST]

**When a package is**
[LIST]
[*] removed through the package manager, it removes the programs and libraries for that package. It leaves the system-wide and per-userid settings.
[*] purged through the package manager, it removes the programs, libraries, AND system-wide settings for that package. It leaves the per-userid settings.
[/LIST]

The package manager isn't important. They each have these capabilities.  1 warning. **[COLOR="#FF0000"]Do not[/COLOR]** use **dpkg** directly to install or remove packages. Only use the package managers, so dependencies are addressed.

Examples of package managers: synaptic, "software center", apt, apt-get, aptitude, and I guess muon. Each different desktop environment flavor can have their own, so there may be more.  I tend to use apt and apt-get. They have slightly different capabilities which are handy, but end-users can use GUIs and accomplish the same things, just slower (the time to launch, search, click, click, click, ok).

---

### Post by Impavidus on 2020-08-02
> **aug7744 said:**
> 
In Linux any software will allways use $HOME to configuration ? If yes allways is an folder with the name of software ?
Simple tools have no config files in HOME, but many big applications have. They are usually in $HOME/.appname or in $HOME/.config/appname or something like that. Note that files/directories with a name starting with a dot are hidden files/directories. File management tools won't show them, unless asked for.

About the only case where you have to run dpkg is when you want to fix the package manager if it's so far broken that apt no longer works. In all other cases apt will call dpkg for you.

---

### Post by aug7744 on 2020-08-03
Thanks for all replies.

---

