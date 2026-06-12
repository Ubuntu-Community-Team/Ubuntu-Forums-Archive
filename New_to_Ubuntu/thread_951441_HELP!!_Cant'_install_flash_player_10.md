---
title: "HELP!! Cant' install flash player 10"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Shippou on 2008-10-18
Hello... the title says it all.

I do installed it manually and also via the repos, but it just won't reflect on firefox.

Any suggestions?

---

### Post by philinux on 2008-10-18
If you're using 386 OS then install from the adobe deb file. dead easy.

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

Remove all other flash first.

---

### Post by Shippou on 2008-10-18
Just a bump post....

Sorry... I'm kinda in a hurry.

---

### Post by Shippou on 2008-10-18
> **philinux said:**
> If you're using 386 OS then install from the adobe deb file. dead easy.

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

Remove all other flash first.

This does not work, sadly.

I mean, it does install, but firefox itself cannot identify that it IS installed after I have logged out/logged in.

Any suggestions?

---

### Post by lswb on 2008-10-18
Try the solution in this thread: 
[http://ubuntuforums.org/showthread.php?t=951194](http://ubuntuforums.org/showthread.php?t=951194)

---

### Post by Shippou on 2008-10-18
Still does not work.

This starts to piss me off now...

---

### Post by philinux on 2008-10-18
What does this command spit out.

locate libflashplayer.so

One thing to try is to backup your FF bookmarks, close FF then rename your .mozilla folder to .mozillabackup. Startup firefox and see if that works. If not revert back to your olde profile folder.

---

### Post by Perfect Storm on 2008-10-18
Try remove and --purge flash first before installing a new version.
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
```

---

