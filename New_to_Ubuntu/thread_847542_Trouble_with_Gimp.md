---
title: "Trouble with Gimp"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Armaniboy on 2008-07-02
I have installed Gimp, however everytime I go to open it, the program closes. I can see it loading and I even tried to reinstall it with the coding:

sudo apt-get install gimp

it didn't work though :(

I'm stumped on how to solve this problem. I also installed Inkscape, that works OK, but it's not the same as Gimp.

Any suggestions?

-Armaniboy-:KS

---

### Post by eapache on 2008-07-02
try```
sudo apt-get purge gimp
```which should remove gimp completely.
Then go to your home folder, press ctrl-H (to show hidden folders) and delete the folder named ".gimp-2.4"
press ctrl-H to hide the hidden folders again then run```
sudo apt-get install gimp
```to reinstall gimp

EDIT - You installed GIMP? How? It is installed by default with Ubuntu.

---

### Post by finer recliner on 2008-07-02
apt-get install gimp wont reinstall it. aptitude will notice that you already have that package install, and will just exit. you should do 
```

apt-get purge gimp
apt-get install gimp

```
to do a reinstall.

another thing to try is launching it from a terminal (just type gimp). when it crashes, you may get an error message back to you that will help diagnose the problem.

---

### Post by Armaniboy on 2008-07-02
I purged it and reinstalled it. Clicked on Graphics -> Gimp....started but then didn't load.

It wasn't until after I typed GIMP in the terminal that it started an installationg screen and I just walked through the steps.

Thank you so much. I greatly appreciate it :KS

---

### Post by Armaniboy on 2008-07-02
This is the error message that I get. I can open it in the terminal, but other than that I can't open it...

/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:10642): LibGimpBase-WARNING **: gimp: wire_read(): error

---

### Post by eapache on 2008-07-02
Try purging it, then delete the config files via my post above, then reinstalling it.

---

### Post by starcannon on 2008-07-02
Solution posted here:
[http://ph.ubuntuforums.com/showthread.php?p=4839612](http://ph.ubuntuforums.com/showthread.php?p=4839612)

I'll put it in a code box here for you:

```
sudo apt-get install --reinstall gimp-gutenprint
```

GL

---

### Post by Armaniboy on 2008-07-02
I did that when you posted that suggestion. I'm only able to open Gimp using the terminal and typing "Gimp" :(

-Armaniboy

---

### Post by starcannon on 2008-07-02
This post tells you how to fix the menu button as well:
[http://ph.ubuntuforums.com/showpost.php?p=4839291&postcount=4](http://ph.ubuntuforums.com/showpost.php?p=4839291&postcount=4)

GL

---

