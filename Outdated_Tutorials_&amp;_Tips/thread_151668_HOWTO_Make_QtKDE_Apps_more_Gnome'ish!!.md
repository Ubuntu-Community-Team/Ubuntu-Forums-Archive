---
title: "HOWTO: Make Qt/KDE Apps more Gnome'ish!!"
date: 2006-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Kimm on 2006-03-28
First of all, I just want to point out that there is a tutorial similar to this allredy. However, I have found a theme that resembles GTK EVEN MORE! Something that I welcomed pretty fast, seeing as I have found a liking for Kdevelop and Kopete, rather than Anjuta and Gaim. 
The theme in question is Troll using the QtCurve control set. The creator sais that this theme is not "Gnome'ish" but rather "Troll'ish" (as in: Trolltech - creators of Qt). A Troll is still quite similar to a Gnome... something you will notice if you follow this guide.

See bottom for screenshots

NOTE: This theme is a KDE Theme, not just a Qt theme. This means that you have to have KDE (or atleast kcontrol) installed in order to use this theme.

if you dont have KDE/KControl installed, type this in your terminal to get it:

sudo apt-get install kcontrol

or, follow the other guide.

**1.** The First thing you would want to do is to download and build QtCurve. Follow this link, and click "download"

[http://www.kde-look.org/content/show.php?content=5065](http://www.kde-look.org/content/show.php?content=5065)

now open a terminal, and type this (in the directory where QtCurve was downloaded):

tar xvzf QtCurve-0.34.tar.gz
cd QtCurve-0.34
./configure
make
sudo make install

If the build was error-free, you should have QtCurve installed now.

**2.** Now we would want to download the acctual theme itself. Follow this link:

[http://www.yeap.de/pub/kde/themes/troll.tar.bz2](http://www.yeap.de/pub/kde/themes/troll.tar.bz2)

click download and place the file wherever you want. To extract it, type this in terminal:

tar xvjf troll.tar.bz2

**3.** Now to acctually install the Troll theme.

1. Run KControl (kcontrol in terminal)
2. Go to Appearances & Themes -> Theme Manager
3. Click on Install New Theme…
4. Go to the directory, where you have extracted troll.tar.bz2 and choose the file Troll.kth
5. Go to Appearances & Themes -> Style
6. Select QtCurve as widget style.
7. Click on Configure…
8. Click on Import… and import the file Troll.qtcurve.

This should set you up with a nice Gnome looking Qt Theme!! :D

Screenshots:

[[IMG]http://img86.imageshack.us/img86/5558/kopetesnap1ld.th.png[/IMG]](http://img86.imageshack.us/my.php?image=kopetesnap1ld.png)
*Kopete 0.12 beta2 in MSN Conversation*
[[IMG]http://img383.imageshack.us/img383/7603/kdevsnap6qo.th.png[/IMG]](http://img383.imageshack.us/my.php?image=kdevsnap6qo.png)
*Repo Kdevelop*

---

### Post by gingermark on 2006-07-27
There is now a [package](http://www.kde-look.org/content/show.php?content=40920) of QTCurve 4.0 for Dapper available.

---

### Post by Thirsteh on 2006-07-27
Use .cpp not .cc please :((((

For the love of conventions!

---

### Post by Hairy_Palms on 2006-07-27
the first link doesnt work kdelook says not found.
the dapper package works though, makes k3b look much better :)

---

### Post by ForksHolder on 2008-05-02
Thanks :)

---

