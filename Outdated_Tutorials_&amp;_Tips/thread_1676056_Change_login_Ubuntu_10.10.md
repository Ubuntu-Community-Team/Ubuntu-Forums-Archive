---
title: "Change login Ubuntu 10.10"
date: 2011-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by joeoshawa on 2011-01-26
I Have looked for this  and it is very hard to find so i thought i would repaste it here the origional tutorial is here.


[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

This tutorial will explain How to change the boot splash screen  (Plymouth’s boot image, or color, behind the “Ubuntu….” logo from purple  to whatever you would like) image for 10.04

Open the terminal and run the following commands[INDENT][HTML]sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow[/HTML][/INDENT]Then logout, and you’ll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.
 When you have logged in after finishing the customizing, run this  command to prevent the Appearance window from opening at the GDM screen  every time.[INDENT][HTML]sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop[/HTML][/INDENT]or
 If you want to install plymouth themes run the following command from your terminal[INDENT][HTML]sudo aptitude install plymouth-theme-*[/HTML][/INDENT]Now you can run the following commands to change login and plymouth screens[INDENT][HTML]sudo update-alternatives --config default.plymouth 
gksu -u gdm dbus-launch gnome-appearance-properties[/HTML]




[/INDENT]

---

