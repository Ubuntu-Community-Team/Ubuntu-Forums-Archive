---
title: "deleting evolution : no desktop"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by noland on 2008-05-10
Hey all... seems i did a really stupid thing (dont we all) since most of the upgrades these days seem to be about the evolution email thingy, and its big upgrades and i have a crappy internet connection, i had the brillant idea to remove it. it now seems i dont have a desktop... well i only have the background and one document on the desktop folder (thanks to that i was able to navigate to the /usr/bin/firefox thingy to have internet) so there is now no toolbar up, nor down, so i have a beautiful background picture, that document and NOTHING... here is what i did...

sudo apt-get remove evolution
sudo apt-get remove evolution-common
sudo apt-get remove evolution-data-server
sudo apt-get remove evolution-data-server-common

well now im to the point i am, ill try reinstalling those things, but i believe i f**** something up with gnome even though i thought i only removed evolution related stuff... hardy 8.04...

any suggestions?

thanks, Phil

---

### Post by joshsmith on 2008-05-10
try 
sudo apt-get install ubuntu-desktop
should get you back a lot of packages, 

however, not having a panel at the top and bottom, could very well just be a different issue
press alt+f2 to get up a run box, and run gnome-panel

if it doesnt work, run 
gnome-terminal
then run gnome-panel inside it, and post any errors

---

### Post by vexorian on 2008-05-10
You can remove evolution and evolution-common

It is a shame you can't remove dataserver, and from the looks of it, it is just a dependency for gnome-panel plugins which is a dependency for gnome panel. I think this is a bug that was introduced by a dependency for just a lame panel applet, really.

---

### Post by noland on 2008-05-10
im trying the 

sudo apt-get install ubuntu-desktop... but at that connection speed, i have 30 mins to wait... but it seems to call back some stuff i deleted... i thought it would have told me some dependencies, but then again i did some autoremove thing which i guess i should not have done... more news later :)

Phil

---

### Post by noland on 2008-05-10
oh well i seem to have a normal desktop after doing

sudo apt-get install ubuntu-desktop

i guess if something else is wrong i will see it later!!

thanks!!

---

