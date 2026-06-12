---
title: "Assigning Startup Applications"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by angusvff on 2013-05-21
I'm Still very new to Linux in general, so bear with me here.

How do you assign start-up applications?
I don't know where to go to find Thunderbird and Transmission to add to the start-up applications.
Or what folder any applications in general.

What Folder is it in?

---

### Post by RockDoctor on 2013-05-21
I copy the appropriate .desktop file from /usr/share/applications to the directory ~/.config/autostart (creating the autostart directory if it does not already exist).

---

### Post by Hadaka on 2013-05-21
Hi, you can easily add start up applications by simply
clicking the star shaped dohickey in the upper right corner
then click " startup applications"
next...click...add
enter the name you want to call it
and then...the application name
click add...repeat for all the applications you want at start up
simple huh?
see attached..

---

### Post by deadflowr on 2013-05-21
You'll need to know the command to execute the applications.
Thunderbird should be just thunderbird, but transmission I think would be transmission-gtk, if you want transmissions gui.

You can test 'em in a terminal, which will either launch the app or not, depending on what you type.

---

