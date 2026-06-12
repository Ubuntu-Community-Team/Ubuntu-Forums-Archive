---
title: "Howto:  Install kpodder and icepodder (Feisty Fawn)"
date: 2007-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by handband2 on 2007-06-12
I was always a fan of [**Juice**]("http://juicereceiver.sourceforge.net/index.php") (an older program to download podcast).  Juice is no longer supported in Linux.  I found two that are, or do identical to what juice use to do.  The first one, icepodder is just a continuing project from Juice.  The other is kpodder which does a lot of the same things that Juice did.

Installing **[COLOR="Red"]kpodder[/COLOR]** (Feisty Fawn)

**Go here to download:  **[COLOR="Red"]  [http://kde-apps.org/content/show.php?content=36630](http://kde-apps.org/content/show.php?content=36630)[/COLOR]

Dependencies:
```
$ sudo apt-get install kdebase-bin kdebase-data kdebase-dev
```

Start installing:
```
$ wget http://kde-apps.org/content/show.php?content=36630

$ tar -jxvf kpodder-0.6.tar.bz2

$ cd ./kpodder-0.6

$ ./configure

$ make

$ sudo make install

$ sudo ln -s /usr/local/kde/bin/kpodder /usr/bin/kpodder
```

Add as application:
```
$ sudo gedit /usr/share/applications/kpodder.desktop
```

Insert into gedit file:
```

[Desktop Entry]
Encoding=UTF-8
Name=KPodder
Exec=kpodder %u
Icon=/usr/local/kde/share/icons/hicolor/32x32/apps/kpodder.png
Type=Application
Categories=Application;AudioVideo;
MimeType=text/rss;text/xml;text/php;application/rss+xml
Comment=A KDE Pocast handler

```

Remove files:
```
$ cd ..

$ sudo rm -Rv kpodder-0.6
 
```




Installing **[COLOR="Red"]icepodder[/COLOR]** (Feisty Fawn)

**Go here to download:**  [http://icepodder.fryingoverajungle.net/?page_id=4](http://icepodder.fryingoverajungle.net/?page_id=4)
or
**Click Here to download:**  [http://icepodder.fryingoverajungle.net/wp-content/uploads/2007/02/icepodder_54-1_all.deb](http://icepodder.fryingoverajungle.net/wp-content/uploads/2007/02/icepodder_54-1_all.deb)

Dependencies:

```
$ sudo apt-get install python python-xmms bittorrent python-wxgtk2.8 python-wxgtk2.6 python-pyrss2gen python-feedparser libwxgtk2.8-0
```

Start installing:

```
$ sudo dpkg -i icepodder_54-1_all.deb
```

Add as application:
```
$ sudo gedit /usr/share/applications/icepodder.desktop
```

Insert into gedit file:
```

[Desktop Entry]
Encoding=UTF-8
Name=IcePodder
Exec=icepodder %u
Icon=/usr/share/icepodder/icons_status/application.ico
Type=Application
Categories=Application;AudioVideo;
MimeType=text/rss;text/xml;text/php;application/rss+xml
Comment=A Gnome Pocast handler
```

Some might have to run the following to get the program icons to show up in the **Applications** > **Sound & Video** list:
```
$ killall gnome-panel
```

---

### Post by dpu-ibrown on 2007-06-19
thanks man good looks.

---

