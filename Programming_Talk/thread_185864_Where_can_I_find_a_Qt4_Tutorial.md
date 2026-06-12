---
title: "Where can I find a Qt4 Tutorial?"
date: 2006-06-01
forum: Programming Talk
---

### Post by Kimm on 2006-06-01
I want to learn Qt4 (note: 4, not 3)

I'm working on a crossplatform application and I have come to the conclution that Qt4 seems like a very robust Framework (even though I've only used one app (Last.fm Player)).

I looked at TrollTechs website, but there where only books, no online tutorials.

Could anyone direct me to one?

---

### Post by njf on 2006-06-01
[http://doc.trolltech.com/4.1/tutorial.html](http://doc.trolltech.com/4.1/tutorial.html)
[http://doc.trolltech.com/4.1/how-to-learn-qt.html](http://doc.trolltech.com/4.1/how-to-learn-qt.html)
[http://doc.trolltech.com/4.1/](http://doc.trolltech.com/4.1/)

---

### Post by asimon on 2006-06-01
Another tutorial can be found at [The Qt 4 Resource Center](http://qt4.digitalfanatics.org/).

---

### Post by Kimm on 2006-06-01
Aahh... Thank you! :D

---

### Post by Kimm on 2006-06-02
Hm... just woundering...

How well do you think Qt4 will cope with future OS's?
I'd want my project to be usable for as long as possible (mainly because there probably will only be one release). I dont care of it cant use graphical effects in the future, I only realy care if it will work.

Right now, 32 bit is my main priority, but I will provide the source so 64 bit is not impossible. However I have got no access to a 64 bit Windows computer, so I cant compile the sources for this, and I have no idea of how well a Qt4 application will work on Windows Vista (++), especially if it was compiled for 32 bit (Windows allredy has compatability issues with older apps).

Does anyone have any info on this?

---

### Post by asimon on 2006-06-02
[QUOTE=Kimm]Right now, 32 bit is my main priority, but I will provide the source so 64 bit is not impossible. However I have got no access to a 64 bit Windows computer, so I cant compile the sources for this, and I have no idea of how well a Qt4 application will work on Windows Vista (++), especially if it was compiled for 32 bit (Windows allredy has compatability issues with older apps).

Does anyone have any info on this?[/QUOTE]
[This page](http://www.trolltech.com/products/qt/features/crossplatform/windows) has some information on it.

---

### Post by quandary on 2008-01-14
Install Qt4

```

sudo apt-get install libqt4-core libqt4-debug-dev libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql lsb-qt4 qt4-designer qt4-dev-tools qt4-doc qt4-qtconfig uim-qt gcc libapt-pkg-perl resolvconf

```

The same applies to all other Qt binaries. 
You will notice above that the canonical 'qmake' is managed by apt alternatives, so before we start to build anything, we will need to set the qmake default to Qt4. 
To return Qt3 to default later you can use the same process.

Sometimes, qmake needs spesifically qt3 or qt4. 
/usr/bin/qmake
/usr/bin/qmake-qt3
/usr/bin/qmake-qt4

the config file is in: 
```

/etc/alternatives/qmake

```

By default, the old qt3 will be used. 
So you need to use apt alternatives to correct this in order for the Qt4 version to be used in all cases:

```

sudo update-alternatives --config qmake
sudo update-alternatives --config uic
sudo update-alternatives --config designer
sudo update-alternatives --config assistant
sudo update-alternatives --config qtconfig
sudo update-alternatives --config moc
sudo update-alternatives --config lupdate
sudo update-alternatives --config lrelease
sudo update-alternatives --config linguist

```

---

### Post by rzrgenesys187 on 2008-08-19
> **quandary said:**
> 
Sometimes, qmake needs spesifically qt3 or qt4. 
/usr/bin/qmake
/usr/bin/qmake-qt3
/usr/bin/qmake-qt4

the config file is in: 
```

/etc/alternatives/qmake

```

By default, the old qt3 will be used. 
So you need to use apt alternatives to correct this in order for the Qt4 version to be used in all cases:


Thanks, I was having trouble compiling until I found this

---

