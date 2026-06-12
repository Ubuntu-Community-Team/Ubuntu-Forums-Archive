---
title: "[SOLVED] help please: problem installing openoffice"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by BeccyBug on 2008-08-18
Hi - sorry if this has been covered elsewhere - I have been searching the forums for days for the help!

Download the 2.4.1 version of openoffice - have uninstalled all version2.3 components with package manager, as instructed to do, somewhere else on the web, and trying to follow the openoffice.org instructions -

am getting the error:

becc@becc-desktop:~/Desktop/OOo241$ sudo ./setup
Checksumming...
Extracting ...
./setup: 466: rpm2cpio: not found
cpio: premature end of archive
find: usr: No such file or directory
basename: missing operand
Try `basename --help' for more information.
/dev/pts/0
Error: Failed to extract the Java Runtime Environment (JRE) files. (exit code 7)

As far as I know I have followed every instruction - installed the Java version 6 update 7 (although the webpage is telling me I have version 4 update 0 installed) - for this I also followed their instructions to the letter!  

Any help gratefully appreciated!  I am sure I am just missing something really dumb!

Thanks in advance

Beccy

---

### Post by Elfy on 2008-08-18
You should download the .deb version - [http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.1](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.1)

The install should be similar to this [http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

IF you need more help come back

Edit - I'll add it here, this shgould all work if you get an error come back
Open a terminal and run

```
cd Desktop
```
```
cd folderwhichhasbeenmade
```you can use tab to autocomplete, so cd O then use tab it should fill in remaining name.

```
cd DEBS
```

```
sudo dpkg -i *.deb
```

```
cd desktop-integration
```

do a dir and change to the folder which looks similar to > openoffice.org-debian-menus_2.4-9268_all.deb. use autocomplete again. Ther should be a .deb in there

```
sudo dpkg -i *.deb
```

---

### Post by BeccyBug on 2008-08-19
Thank you so much for that - it worked a treat - don't know that I will ever understand all these codes!  So dpkg is unpacking the *.deb that has some kind of installation files in it?  The stcman installation page was the one I'd found yesterday, but would have struggled to find it again, but your instructions were muchly easier to follow!  

Thanks again :KS

Beccy

---

### Post by Elfy on 2008-08-19
Glad it helped and welcome to the forums - the commands basically do as you say, you can find out more using the manual pages in a terminal. You will understand what they do in the end, I did.

man dpkg

You also need to have root rights to do so which is what sudo is for, use it when you need root rights and if the command runs in a terminal. If you need to run a GUI as root - like the file manager for instance, use gksudo.

---

### Post by BeccyBug on 2008-08-19
Slowly picking it up as I go along, but I'm only a week old - still, it's something to distract me from schoolwork during the holiday!  Been meaning to try it for years!  Now I just need to figure out the file sharing to make this really work for me in everyday life!  I'll get there!

Thanks again

Beccy

---

