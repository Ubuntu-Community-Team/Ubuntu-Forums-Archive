---
title: "How to display the volume bar in Lubuntu?"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by lonrot on 2015-01-22
I noticed that Linux Mint and Elementary OS have a volume bar that pops whenever you press a volume key on your keyboard.

This feature is also similar to Mac OSX which comes along with popping sounds.

How can I enable this on Lubuntu 14?

---

### Post by ajgreeny on 2015-01-22
Not sure what you mean by a volume bar; is it **on-screen notification** of some sort?

---

### Post by lonrot on 2015-01-22
> **ajgreeny said:**
> Not sure what you mean by a volume bar; is it **on-screen notification** of some sort?

Exactly, is not a permanent element, it only appears when pressing volume keys.

---

### Post by Dennis N on 2015-01-22
There is a bug report (or feature request?) on this since 2012, but it is still at "confirmed" status.

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1005542](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1005542)

---

### Post by lonrot on 2015-01-22
> **Dennis N said:**
> There is a bug report (or feature request?) on this since 2012, but it is still at "confirmed" status.

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1005542](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1005542)

Thanks for the information.

I was able to get around this by installing [**notify-osd** and** xfce4-volumed gstreamer0.10-alsa**]("http://askubuntu.com/questions/74230/how-to-get-xfce4-volumed-to-work-in-lubuntu").

The design is quite instrusive, but it works ;)

Maybe the [volume meter from Elementary OS]("http://www.webupd8.org/2012/04/pantheon-notify-new-notification-daemon.html") could be installed in Lubuntu.

It's way more elegant.

---

