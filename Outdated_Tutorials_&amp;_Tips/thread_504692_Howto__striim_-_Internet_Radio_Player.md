---
title: "Howto:  striim - Internet Radio Player"
date: 2007-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by handband2 on 2007-07-19
Thanks to Mystilleef - [http://ubuntuforums.org/showthread.php?t=436709](http://ubuntuforums.org/showthread.php?t=436709)

**[SIZE="3"]Here is a step by step howto for [striim - Internet Radio Player]("http://striim.sourceforge.net/").[/SIZE]**

```
$ sudo apt-get install build-essential yelp python-dbus python-gtk2 python-gtk2-dev python-gnome2 python-musicbrainz2 python-gst0.10 gstreamer0.10-plugins-base gstreamer0.10-plugins-ugly
```

Download file from here:  [http://striim.sourceforge.net/download.php](http://striim.sourceforge.net/download.php)
or
```
$ wget http://striim.sf.net/striim-0.0.4.tar.bz2
```

```
$ tar -jxvf striim-0.0.4.tar.bz2
```

```
$ cd striim-0.0.4/
```

```
$ ./configure
```

```
$ make
```

```
$ sudo make install
```

now go to [B][SIZE="3"]Applications -> Sound & Video -> striim Internet Radio Player
[/SIZE][/B]

---

