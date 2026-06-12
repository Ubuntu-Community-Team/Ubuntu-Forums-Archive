---
title: "fluxbox-generate_menu &amp;&amp; convertkeys"
date: 2005-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by drogoh on 2005-07-30
As being a Fluxbox user, I was a bit baffled when I went to generate a menu for the first time within Ubuntu (lost my three year old files, d'oh!) and lo and behold, there was no fluxbox-generate_menu!  I did some investigating and found that it is actually installed but is not packaged correctly and therefore not installed correctly.  To regain the functionality of both fluxbox-generate_menu and convertkeys, do the following:

```
Open your favorite terminal.

cd /usr/share/doc/fluxbox
sudo gunzip fluxbox-generate_menu.gz
sudo gunzip convertkeys.gz
sudo chmod 755 fluxbox-generate_menu convertkeys
sudo mv fluxbox-generate_menu /usr/bin
sudo mv convertkeys /usr/bin
```

Voila! You will have these two seemingly small but quite useful scripts back in use.  It can make for a big help with new users to Fluxbox on Ubuntu, especially when asking "where's the menu?"


Note:  This was tested with the backports 0.9.13 version, I do not know if it is limited to just the backports or if  the 0.9.11 in universe/x11 has the same problem.

---

### Post by tane_stelzer on 2005-12-29
i get the error
/usr/bin/fluxbox-generate_menu:line 796: random_color: command not found
i did everything you said
tane

---

### Post by Anubis on 2007-11-12
No fluxbox-generate_menu.gz script at all, on my Gutsy system. How lame is that?

---

### Post by D_Murdock on 2007-12-11
Same here....

---

### Post by yabbadabbadont on 2007-12-11
RedSquirrel has an excellent tutorial that addresses these issues:

[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

---

