---
title: "How to build Memoranda"
date: 2006-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by ryu kun on 2006-10-01
_Correction:_ *Technically, it's not "building" as the last version is prebuilt. I'll explain here just how to install it.*

Memoranda (formerly known as jNotes2) is an open source cross-platform diary manager and the tool for scheduling personal projects.
Homepage: [http://memoranda.sourceforge.net/index.html]("http://memoranda.sourceforge.net/index.html")

_Some alternatives:_
[Zim]("http://pardus-larus.student.utwente.nl/~pardus/projects/zim/") : a desktop wiki for Gnome.
[Tomboy]("http://www.gnome.org/projects/tomboy/") : a desktop note-taking application for Linux and Unix.
[Basket]("http://basket.kde.org/") : a note taker, organizer for KDE (embeddable into Kontact)

[SIZE="4"]A. How to install[/SIZE]

--> Firstly, to add extra repositories to your default Ubuntu installation, read [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories").

Get Java Runtime Environment (yes it's a Java program) and make sure Java is well configured:

```
sudo aptitude update
sudo aptitude install sun-java5-jre
sudo update-java-alternatives --jre --set java-1.5.0-sun
```

Let's create a directory for memoranda.
```

cd ~
mkdir memoranda
cd memoranda
```

Now we'll download Memoranda. Current version is 1.0 RC3. To get it

```
wget http://prdownloads.sourceforge.net/memoranda/memoranda1.0-rc3-20060703.zip
tar -xvf memoranda1.0-rc3-20060703.zip
```

or check [this page]("http://prdownloads.sourceforge.net/memoranda") to get latest release and extract it.

As its prebuilt, you can run Memoranda by memoranda.sh script. To make it executable, run this:

```
chmod +x memoranda.sh
```

You can run it with a doubleclick in nautilus. If it doesn't work, right click on it and check its permissions and make it executable.

Alternatively, run this:

```
sh memoranda.sh
```

----------------------------
a note from the README file:

> NOTE FOR NON-KDE UNIX USERS: You can safely remove the systray4j startup line from memoranda.sh to avoid any unknown but possible nasties.
----------------------------



[SIZE="4"]B. How to add a shortcut to the panel[/SIZE]


_**Warning:**_ Don't forget to modify "MEMORANDA_DIR" expressions below with the path of your actual memoranda directory (e.g. "/home/ryu/src/memoranda")
 
If you'd like to add Memoranda's link to the Gnome panel,

```
cd MEMORANDA_DIR
gedit memoranda.sh
```

add this line below the first line:

```
cd MEMORANDA_DIR
```

Save and exit.

Drag and drop memoranda.sh file to your Gnome panel.

---------------

If you'd like to change its panel icon first run this:

```
sudo cp /MEMORANDA_DIR/lib/icons/m* /usr/share/pixmaps/
```

then right click its icon on the panel and select properties, click on the Icon and choose memoranda's icons.

Enjoy! 8)

---

### Post by ryu kun on 2006-11-28
-please delete this post-

---

### Post by Ederico on 2007-03-07
Thanks for the instructions. I installed it, looks great. Now I will have to get a hand on it. Useful application. :)

---

### Post by Wooksta on 2007-03-18
Thanks for the tutorial, nice work :)

---

