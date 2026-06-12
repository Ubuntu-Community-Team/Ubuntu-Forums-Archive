---
title: "HOWTO Replace xmessage by gxmessage the Debian way"
date: 2007-03-09
forum: Outdated Tutorials &amp; Tips
---

### Post by synss on 2007-03-09
Hello, for my first post, I will propose a somehow involved tip:
Replace xmessage by gxmessage **the Debian way**, which is obviously the only correct way but...

First things first, have a look at [gxmessage]("http://freshmeat.net/projects/gxmessage"), a pretty GTK2-based xmessage clone, which I like better for obvious reasons: it is pretty and fast.
Like it? install it:
```
sudo apt-get install gxmessage
```
and try it 
```
gxmessage -center -nofocus -timeout 5 -button yes,no,maybe -file /var/log/syslog
```
like it? OK but how to replace that good old xmessage, in a way that will really works?
```
sudo -s
dpkg-divert --divert /usr/bin/xmessage.X11 --rename /usr/bin/xmessage
update-alternatives --install /usr/bin/xmessage x-messaging-system /usr/bin/xmessage.X11 50
update-alternatives --install /usr/bin/xmessage x-messaging-system /usr/bin/gxmessage 55
exit
```

The first line starts a root shell because all commands need to be executed as root and I am a lazy typist. The second line move xmessage out of the way and so that /usr/bin/xmessage will be left untouched by an update of the xmessage package. Next two lines, we tell the Debian system that there exists two possibilities for running xmessage, one being the X11 version and one being the GTK2 version, since the second one has a higher priority, it will be prefered by default. 
Use
```
sudo update-alternatives --display x-messaging-system
```
to see what the system knows
and 
```
sudo update-alternatives --config x-messaging-system
```
for reverting to xmessage, while leaving you the possibility to change your mind once more.

Note the for echoing into (g)xmessage, you need to use -file hyphen```
echo "me me me" | xmessage -file -
```

Debian is a nice system.

This tip works for any replacement you would have in mind.

references:
man update-alternatives
[http://www.debian.org/doc/FAQ/ch-customizing.en.html](http://www.debian.org/doc/FAQ/ch-customizing.en.html)

---

