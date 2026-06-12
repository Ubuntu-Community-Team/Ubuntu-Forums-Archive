---
title: "HOWTO: Custom Rhythmbox Icons"
date: 2006-09-17
forum: Outdated Tutorials &amp; Tips
---

### Post by escape on 2006-09-17
*Note: this no longer changes everything on Rhythmbox 0.9.6. Specifically, the icons for podcast and rhythm-box-tray-icon in /usr/share/rhythmbox/art no longer update... working on it though.*

This script will change your rhythmbox (and possibly other media player) icons, while making backups of the originals in ~/iconbackups. 

Download the attachment at the bottom of this post to your home directory. Then, ```

tar -xvf ~/icons.tar.gz
cd ~/icons
chmod 755 script.sh
./script.sh

```

The play/back/forward/volume/shared library icons require the OSX 3.1 icon set, availible at gnome-look.org. I included the shared library icon, called wtf.png, if you're feeling adventurous and want to search for where it should go. If you don't like these icons, use your own (put the ones you want in ~/icons with the same names as the original ones and run the script agan). Also, if you find some better icons, like the actual iTunes ones, please post them here!


Screenshot:
[[IMG]http://img166.imageshack.us/img166/4787/screenshotuy6.th.png[/IMG]](http://img166.imageshack.us/my.php?image=screenshotuy6.png)

---

### Post by Janux on 2006-09-18
Hum... I believe that more than a sec has passed :)

---

### Post by escape on 2006-09-19
Ok, one *more* sec.

---

### Post by Zhukov on 2006-09-25
What?

---

### Post by escape on 2006-10-07
It took me a while to get the script up (internet issues here).

---

### Post by Janux on 2006-10-09
To change the tray, you need to place your custom image at your icon theme.
I put mine at /usr/share/icons/Human/22x22/apps/rhythmbox-tray-icon.png and it works.

---

### Post by Psyphre on 2008-11-24
very very very very old topic i know, but the method suggested by Janux no longer works with the recent versions of rhythmbox. Just wondering if anyone knows how to do it now?

Thx

---

