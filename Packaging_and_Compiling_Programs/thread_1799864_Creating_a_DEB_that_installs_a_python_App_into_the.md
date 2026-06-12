---
title: "Creating a DEB that installs a python App into the Applications Menu"
date: 2011-07-08
forum: Packaging and Compiling Programs
---

### Post by Tony Flury on 2011-07-08
I have written a simple Python game - and i want to create a DEB for the game that will 
1) install the game script into /usr/game (I think i have that bit down), 
2) Will also install a launcher into the Application -> Games menu.

It is this second bit that has confused me thoroughly - it is not obvious to me how i add something to a menu,  where i need to put my launcher file, icon etc to make this all work. Any hints/guides/how-tos.

---

### Post by mr bob on 2011-07-08
I've written a couple of projects in python and created deb installers for them.

In short you need a small text config file in /usr/share/applications called $name.desktop ($name being whatever is the name of your app)

Take a look on your computer at the .desktop files in /usr/share/applications. This will give you an idea of how to produce your own that you can add into your deb installer, including how to include an icon.

Hope this helps.

---

