---
title: "HOWTO:run runecape on iced tea amd64"
date: 2007-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by erlinux on 2007-11-24
1._ get the right version of iced tea, normal version from default repo wont work_

from the terminal type this

Code:

sudo gedit /etc/apt/sources.list

then copy and paste this at the bottom of the file.

Code:

# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

save it, exit out of gedit 

go to synaptic and search iced tea
install
icedtea-java7-jre
icedtea-java7-bin
icedtea-java7-plugin

2. _running runescape_

go to runescape.com

when runescape ask for high detail or low detail, scroll down 

it will say "Select Java Version - only change this if the default doesn't work"

select "unsigned applet using default java" 

click whatever detail button BELOW the java type selection

then do whatever you, runescape runs absolutely the same except when starting up the font is different, but that goes away one its loaded

---

### Post by mig5 on 2007-11-27
> **erlinux said:**
> ...
select "unsigned applet using default java" 

click whatever detail button BELOW the java type selection

then do whatever you, runescape runs absolutely the same except when starting up the font is different, but that goes away one its loaded

Runescape won't run exactly the same if the unsigned applet option is selected, seeing as none of the data that the runescape applet downloads will be cached for the next use, so every time you play you will be loading the entire game again.  This means that everytime you enter an area of the map you will have to wait for the map data to load as well as the usual server loading bit.
Basically it will work, but you will find that the loading takes a lot longer compared to using a signed applet.

---

