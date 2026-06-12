---
title: "How to install Vuze in Maverick and Natty"
date: 2011-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by shantiq on 2011-03-22
[SIZE=3][B]how to install vuze in maverick and natty
=========================


[/B]The version in the repository often does not start for many people so here is an alternative route


[B][FONT=Courier New][SIZE=2]

[/SIZE][/FONT][/B][/SIZE][B][FONT=Courier New][SIZE=2][COLOR=#000000]1.  [/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=2]First[/SIZE][/FONT][FONT=Courier New][SIZE=2][COLOR=#000000]


[/COLOR][/SIZE][/FONT][/B]```
 [FONT=Courier New] sudo add-apt-repository ppa:sun-java-community-team/sun-java6[/FONT]
```[B][FONT=Courier New][SIZE=2][COLOR=#000000]



At this point go to software-sources and edit
the word natty for maverick on both lines if you are using natty as there are no packages yet for natty

[/COLOR][/SIZE][/FONT][/B]```
 [FONT=Courier New]sudo apt-get update[/FONT]
```[B][FONT=Courier New][SIZE=2][COLOR=#000000]

[/COLOR][/SIZE][/FONT][/B]```
 [FONT=Courier New] sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk[/FONT]
```[B][FONT=Courier New][SIZE=2][COLOR=#000000]
===========================================[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=2]

[/SIZE][/FONT][/B] [COLOR=#000000][FONT=Times New Roman][FONT=Verdana][B][FONT=Courier New][SIZE=2]2. THEN


[==> ]("http://cf1.vuze.com/files/Vuze_Installer.tar.bz2")[/SIZE][/FONT][/B][FONT=Arial Black][SIZE=2][download]("http://cf1.vuze.com/files/Vuze_Installer.tar.bz2")[/SIZE][/FONT][B][FONT=Courier New][SIZE=2] to home folder

3. Then create a launcher on desktop (right-click create launcher) 

and Go to where you have stored your download and use the commandline instruction[/SIZE][/FONT]


[/B][/FONT][/FONT][/COLOR]```
 **./azureus**
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana][B][FONT=Courier New][SIZE=2]


see    attached image
[/SIZE][/FONT][/B]

[/FONT][/FONT][/COLOR]

---

### Post by bsmith1051 on 2011-03-24
Thanks for the clear instructions!  Which version is this, though?  I was hoping to find a PPA somewhere so that I would automatically receive updates.

Also, do you know if the Ubuntu/Linux version of Vuze supports all the same media-device features as under Windows?  Specifically, I am hoping to setup Vuze on Ubuntu 10.10 to automatically share downloads to my Tivo.

---

### Post by shantiq on 2011-03-25
4.3.0.6-1.1ubuntu1
and sorry do not know the answers to your other questions

---

