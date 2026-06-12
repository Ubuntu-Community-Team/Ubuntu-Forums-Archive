---
title: "OpenOffice crashes on save/saveas using hardy"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Famous Sheamus on 2008-06-28
Openoffice 2.4 is crashing upon save/saveas.  Application goes gray on screen and I can't even type in a file name or indicate what type a file to save it as.  This happens both with word processor and presention "powerpoint"  I haven't had a chance to experiment with other apps. yet.  I am new to unbuntu so it's ok to treat me as "don't have a clue".  New computer with Ubuntu Hardy Heron has been running great with no problems for about a month.  If I knew how to back out updates I would go back about a week and try it as it was working fine last time I used program.  Any help would be appreciated.

---

### Post by braddcadd on 2008-07-14
Have you tried un-installing open-office and re-installing?

Applciations->Add/Remove-> (type "openoffice" in the search box)
Uncheck the unstalled packages then apply the changes

Do it in reverse to install them again.  HTH

---

### Post by zozio32 on 2008-07-15
Same problem for me, but it extends to Gimp 2.5 and Inkscape. I can open a file in any of the 3 application by going the file icon --> right click --> open with "the desired stuff", but I can't open anything from the application itself. And I can't save anything... :(
I supected it was a problem related to my java installation as it appears after I uninstall *OpenJDK* to keep only the *sun java stuff*. But I've re-install everything since, and the problem is not solved.
I have also uninstalled OpenOffice.org and re-installed it from the package manager, but I still have the same issue.

Does it make any difference to Add/Remove an application with:
Applciations->Add/Remove-> (type "openoffice" in the search box) ?
Any help would be appreciated.

---

### Post by braddcadd on 2008-07-15
See if you have any broken packages.  Try this in a terminal:
```
sudo apt-get check
```

---

### Post by silkstone on 2008-07-15
If you think that the problem is java related, you could do a reinstall...

sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin

At some stage during the above you need to accept the java licence, and to do this you use the arrow keys to highlight 'Yes'. Sorry if you already know all this!

---

### Post by zozio32 on 2008-07-15
well,

I've tried what you told me.
```
sudo apt-get check
```
this didn't do much, it gone trough the stuff, printing done without any interesting message.

Then, I've tried the
```
sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```
I've got trough the license things, but the console got stuck, dispaying the following message:
```
sun-java6-jre not found
``` (or something equivalent.
I've checked on the *synaptic package manager*, sun-java6-jre is installed. I've added *sun-java6-plugin* and *sun-java6-source*.

and, OpenOffice still crash as soon as I try to open a file from the application.

It must be something else than java

I'll try a *complete removal* of OpenOffice from the package manager, and I'll give the results

---

### Post by zozio32 on 2008-07-15
I manage to get openOffice and Gimp working properly (at first glance) :D,
by doing a *complete removal* and re-installation of both. SOmething with the configuration file was probably wrong.

but...

I've applied the same method to Inkscape and I still have the same problem... :confused:

---

### Post by Hagar Delest on 2008-07-16
For OOo, you can also try to rename your OOo user profile (~/.openoffice.org2). A new profile will be created with brand new configuration files.

---

### Post by zozio32 on 2008-07-18
I've just realize that *Revelation*, the password manager, suffers from the same stuff: if I try to open a revelation file from the application, the window just closes itself without any warning...
I've tried to uninstall it fully and reinstall it, but that doesn't change anything.
I am getting a bit hopeless with this problem :mad:

---

