---
title: "Howto: Creating Multiple Wine Configurations"
date: 2006-08-02
forum: Outdated Tutorials &amp; Tips
---

### Post by tuxcantfly on 2006-08-02
Crossover office has a nifty little thing called bottles, which causes apps to be installed in their own fake windows drives. This is useful, as it helps prevent software conflicts. Wine, on the other hand, doesn't provide a nice gui to create them, but you can, with a few shell scripts. Let's say you have 2 apps: app1 and app2. App1 needs wine to be set to windows 98, while app2 needs windows 2000. Normally, you'd be out of luck, as it'd try to install both into the same fake windows drive, ~/.wine, and they'd conflict. Here's the solution: install app1 as usual. This would be something like:

**wine installapp1.exe**

Replace installapp1 with the setup file. Once you're done with installation, do this:

**mv .wine .app1**

Do the same thing for app2:

**wine installapp2.exe**

**mv .wine .app2**

If you have any more applications to install, just continue the process. Now, let's create the shell scripts:

**sudo gedit /usr/bin/startapp1**

Kubuntu users should substitute kate for gedit, others should use nano. In this empty file, enter:

[I]export WINEPREFIX="~/.app1"
cd ~/.app1/drive_c/Program\ Files/app1
wine app1.exe[/I]

Substitute the application name, paths, and files accordingly. Now, make it executable:

**sudo chmod +x /usr/bin/startapp1**

Do the same thing for app2 and the rest:

**sudo gedit /usr/bin/startapp2**

[I]export WINEPREFIX="~/.app2"
cd ~/.app2/drive_c/Program\ Files/app2
wine app2.exe[/I]

**sudo chmod +x /usr/bin/startapp2**

Now, you should be able to start app1 with the command startapp1, and you should be able to start app2 with the command startapp2. If that's not enough, you can add in an infinite number of additional apps by repeating the process.

---

### Post by mytharak on 2011-02-27
How would one get winecfg to set options for each of these "bottles?"

---

