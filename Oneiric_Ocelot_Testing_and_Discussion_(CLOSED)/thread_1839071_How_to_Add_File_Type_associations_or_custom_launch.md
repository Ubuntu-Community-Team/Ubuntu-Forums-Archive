---
title: "How to Add File Type associations or custom launchers in 11.10?"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cor2y on 2011-09-04
Is this because its the beta or is there a hidden setting that has to be enabled?

For example alacarte aka Main Menu doesnt work for creating custom launchers, or right clicking on the desktop "Create Launcher" seems to be missing from the menu selection.

Finally file associations, for example i installed gnome split via ppa, but i cant get .001 files to associate   i right click on the file select "Open With Other Application"  theres a big heading that says "No Application Available to Open Test.zip.001 Click Show Other Applications or Find Application Online to install new Application" however gnome split isnt listed in the installed apps even though its installed and theres no way to point to it manually nor does 11.10 find an app online that i can use.

---

### Post by mc4man on 2011-09-04
You can bring back the "Create Launcher"  in several ways and even create a launcher to pop it up - a couple of threads on

[http://ubuntuforums.org/showthread.php?t=1837224&highlight=create+launcher](http://ubuntuforums.org/showthread.php?t=1837224&highlight=create+launcher)
[http://ubuntuforums.org/showthread.php?t=1815051&highlight=create+launcher](http://ubuntuforums.org/showthread.php?t=1815051&highlight=create+launcher)

As far as file associations - if need be just add to ~/.local/share/applications/mimeapps.list

Direct access to adding/using custom commands, either thru the r. click context or the default apps dialogs has been removed in gnome/nautilus 3
In those cases just approach from opposite direction - in the past using a custom command created a .desktop and maybe also added to mimeapps.list
So now just create the .desktop w/ an Exec= using your command, add it to mimeapps.list if applicable and you'll have use of the custom command

Just one small ex. - I have 2 custom .desktops that allow proper autoplay of audio cd's w/ audacious and vlc - screen shows added to System Settings > removable media

Also in unity quicklists can execute any custom command that will run in Alt+F2 and or any script.
So there are many ways to do as you please...

---

### Post by cor2y on 2011-09-05
Thank you for the info and help. 
I had forgotten about the .desktop files and the mimeapps.list i havent had to deal with those things since the days of 5.10 and 6.04

---

