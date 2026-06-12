---
title: "Building source package and package"
date: 2012-04-30
forum: Packaging and Compiling Programs
---

### Post by zooey on 2012-04-30
Hi guys,

i tried to create source and package to submit into ubuntu package repository, i built the .deb package but they want from me some source package, could you please someone explain me how to build that source package or .deb package properly, i know that stuff like dh_make etc..

For example i have my project in directory Project:
/project
under that directory i have structure like this:
/icons
/config
/database
skript.pl
If i issue now all that dh_make, i configure description etc...and then issue dbuild, it won't make me structure like should be for example that script.pl should be in /opt/project/bin/script, icons in /opt/project/icons etc.., where i should wrote commands to build appropriate structure, to makefile or to rules file or what, and if do you have some good book on this, because what i already saw on debian or ubuntu docs wasn't very helpful...it was too concise or too difficult and without comments, Thanks

---

### Post by r-senior on 2012-05-01
Don't you just need to do 'debuild -S' to create a signed source package?

---

### Post by zooey on 2012-05-01
Hmm,

i don't know. If i am guessing so when i have structure like i wrote, i will make project.orig.tar.gz at first, i will have my project folder + that project.orig.tar.gz , than run debuild -S which will produce .diff, .dsc etc... than run dh_make, fill in description etc... in rules file i have to define commands for changing my original folder structure to desired structure of binary package and than run pbuilder to create package?

---

