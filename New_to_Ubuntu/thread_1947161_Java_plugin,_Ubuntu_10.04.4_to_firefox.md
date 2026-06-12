---
title: "Java plugin, Ubuntu 10.04.4 to firefox ?"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by jaho22 on 2012-03-26
How to install java-plugin to firefox on latest ubuntu 10.04 update 4 ?

---

### Post by Perfect Storm on 2012-03-26
Moved to Beginners forum.

---

### Post by mrcanard on 2012-06-13
Thanks for the linkage.

---

### Post by Zill on 2012-06-13
Open a Terminal and enter the following command:
```
sudo apt-get install ubuntu-restricted-extras
```
This will install many useful "extras", such as support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, **[COLOR="Red"]Java runtime environment[/COLOR]**, Flash plugin, LAME (to create compressed audio files), and DVD playback.

This includes the IcedTea plugin, which is a web browser plugin to execute Java applets.

---

