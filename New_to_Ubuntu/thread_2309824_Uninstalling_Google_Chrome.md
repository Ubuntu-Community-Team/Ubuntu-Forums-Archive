---
title: "Uninstalling Google Chrome?"
date: 2016-01-13
forum: New to Ubuntu
---

### Post by Daveski17 on 2016-01-13
I have installed Google Chrome on my laptop, I ran Chromium before. I believe if I want to uninstall it for any reason I type this into the Terminal: sudo apt-get remove google-chrome-stable

Is this true?

Thanks, Dave.

---

### Post by vasa1 on 2016-01-13
> **Daveski17 said:**
> I have installed Google Chrome on my laptop, I ran Chromium before. I believe if I want to uninstall it for any reason I type this into the Terminal: sudo apt-get remove google-chrome-stable

Is this true?

Thanks, Dave.

Yes. Or you could use *sudo apt-get purge google-chrome-stable* ([https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)). And you can always run a simulation first using *-s*:
*apt-get purge -s google-chrome-stable* and *sudo* isn't needed when running with *-s*.

---

### Post by Daveski17 on 2016-01-13
OK thanks Vasa. I appreciate the reply.

---

### Post by vasa1 on 2016-01-13
Even with *purge*, files and folders created by Google Chrome will remain in your home folder. For example, I have:
/home/vasa1/.config/google-chrome
and
/home/vasa1/.cache/google-chrome

Then, you can also get rid of Google Chrome's ppa by going into your "Software Sources" and removing entries related to Google Chrome in the "Other Software" tab.

---

### Post by cariboo on 2016-01-14
I'd suggest using [ppa-purge]("http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html") to remove ppa's and revert back to the default packages.

---

### Post by vasa1 on 2016-01-14
> **cariboo said:**
> I'd suggest using [ppa-purge]("http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html") to remove ppa's and revert back to the default packages.
In this particular case, I'm not sure there's any default package to revert to. Plus, is it still correct that ppa-purge is restricted to [ppas from ppa.launchpad.net]("http://askubuntu.com/a/168198/")?

Also, there's this answer to ["Difference between "ppa-purge” and “add-apt-repository -r"?"]("http://askubuntu.com/a/309973/")

---

### Post by Daveski17 on 2016-01-14
> **vasa1 said:**
> Even with *purge*, files and folders created by Google Chrome will remain in your home folder. For example, I have:
/home/vasa1/.config/google-chrome
and
/home/vasa1/.cache/google-chrome

Then, you can also get rid of Google Chrome's ppa by going into your "Software Sources" and removing entries related to Google Chrome in the "Other Software" tab.

OK thanks. I know Chrome can be difficult to totally uninstall on any OS. I was initially reluctant to download Chrome because of this but the Pepper Flash hadn't been updated for Chromium for a while and I didn't know what was going on. At least I don't have to worry about that anymore lol. ;)

---

### Post by vasa1 on 2016-01-14
> **Daveski17 said:**
> ... I know Chrome can be difficult to totally uninstall on any OS. ...
I've not come across reports of that on Linux desktops. I remember, from my MS Windows days, reading about the difficulty of getting rid of Google Updater (or something like that).

---

### Post by Daveski17 on 2016-01-14
> **cariboo said:**
> I'd suggest using [ppa-purge]("http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html") to remove ppa's and revert back to the default packages.

OK, thanks. Can Chrome be completely removed from Ubuntu easily?

---

### Post by Daveski17 on 2016-01-14
> **vasa1 said:**
> I've not come across reports of that on Linux desktops. I remember, from my MS Windows days, reading about the difficulty of getting rid of Google Updater (or something like that).

From what I can recall Chrome leaves folders all over the place on Windows. Do you think after uninstalling Chrome from Ubuntu there are any problems with the folders left behind? Or are they in the main pretty innocuous?

---

### Post by deadflowr on 2016-01-14
> **Daveski17 said:**
> From what I can recall Chrome leaves folders all over the place on Windows. Do you think after uninstalling Chrome from Ubuntu there are any problems with the folders left behind? Or are they in the main pretty innocuous?

You can always double check.
Here is where google-chrome-stable installs all files (outside of Home)
via dpkg-query --listfiles google-chrome-stable:
```
/./usr
/usr/bin
/usr/share
/usr/share/gnome-control-center
/usr/share/gnome-control-center/default-apps
/usr/share/gnome-control-center/default-apps/google-chrome.xml
/usr/share/applications
/usr/share/applications/google-chrome.desktop
/usr/share/doc
/usr/share/doc/google-chrome-stable
/usr/share/doc/google-chrome-stable/changelog.gz
/usr/share/doc/google-chrome
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/google-chrome.1
/usr/share/menu
/usr/share/menu/google-chrome.menu
/etc
/etc/cron.daily
/opt
/opt/google
/opt/google/chrome
/opt/google/chrome/product_logo_32.png
/opt/google/chrome/locales
/opt/google/chrome/locales/nb.pak
/opt/google/chrome/locales/zh-CN.pak
/opt/google/chrome/locales/ja.pak
/opt/google/chrome/locales/bg.pak
/opt/google/chrome/locales/fil.pak
/opt/google/chrome/locales/et.pak
/opt/google/chrome/locales/vi.pak
/opt/google/chrome/locales/hr.pak
/opt/google/chrome/locales/de.pak
/opt/google/chrome/locales/pl.pak
/opt/google/chrome/locales/sw.pak
/opt/google/chrome/locales/am.pak
/opt/google/chrome/locales/en-US.pak
/opt/google/chrome/locales/bn.pak
/opt/google/chrome/locales/lv.pak
/opt/google/chrome/locales/da.pak
/opt/google/chrome/locales/ar.pak
/opt/google/chrome/locales/hi.pak
/opt/google/chrome/locales/ro.pak
/opt/google/chrome/locales/es-419.pak
/opt/google/chrome/locales/fr.pak
/opt/google/chrome/locales/te.pak
/opt/google/chrome/locales/ms.pak
/opt/google/chrome/locales/pt-BR.pak
/opt/google/chrome/locales/tr.pak
/opt/google/chrome/locales/pt-PT.pak
/opt/google/chrome/locales/ko.pak
/opt/google/chrome/locales/ru.pak
/opt/google/chrome/locales/zh-TW.pak
/opt/google/chrome/locales/ml.pak
/opt/google/chrome/locales/th.pak
/opt/google/chrome/locales/sk.pak
/opt/google/chrome/locales/it.pak
/opt/google/chrome/locales/he.pak
/opt/google/chrome/locales/mr.pak
/opt/google/chrome/locales/el.pak
/opt/google/chrome/locales/id.pak
/opt/google/chrome/locales/sv.pak
/opt/google/chrome/locales/hu.pak
/opt/google/chrome/locales/cs.pak
/opt/google/chrome/locales/kn.pak
/opt/google/chrome/locales/lt.pak
/opt/google/chrome/locales/sr.pak
/opt/google/chrome/locales/sl.pak
/opt/google/chrome/locales/en-GB.pak
/opt/google/chrome/locales/fa.pak
/opt/google/chrome/locales/ta.pak
/opt/google/chrome/locales/gu.pak
/opt/google/chrome/locales/uk.pak
/opt/google/chrome/locales/ca.pak
/opt/google/chrome/locales/fi.pak
/opt/google/chrome/locales/nl.pak
/opt/google/chrome/locales/es.pak
/opt/google/chrome/chrome_material_100_percent.pak
/opt/google/chrome/libwidevinecdm.so
/opt/google/chrome/product_logo_256.png
/opt/google/chrome/default-app-block
/opt/google/chrome/chrome
/opt/google/chrome/xdg-mime
/opt/google/chrome/snapshot_blob.bin
/opt/google/chrome/product_logo_32.xpm
/opt/google/chrome/nacl_irt_x86_64.nexe
/opt/google/chrome/default_apps
/opt/google/chrome/default_apps/search.crx
/opt/google/chrome/default_apps/gmail.crx
/opt/google/chrome/default_apps/external_extensions.json
/opt/google/chrome/default_apps/drive.crx
/opt/google/chrome/default_apps/youtube.crx
/opt/google/chrome/default_apps/docs.crx
/opt/google/chrome/chrome-sandbox
/opt/google/chrome/libwidevinecdmadapter.so
/opt/google/chrome/nacl_helper_bootstrap
/opt/google/chrome/product_logo_64.png
/opt/google/chrome/product_logo_48.png
/opt/google/chrome/product_logo_128.png
/opt/google/chrome/resources.pak
/opt/google/chrome/product_logo_22.png
/opt/google/chrome/chrome_material_200_percent.pak
/opt/google/chrome/PepperFlash
/opt/google/chrome/PepperFlash/manifest.json
/opt/google/chrome/PepperFlash/libpepflashplayer.so
/opt/google/chrome/cron
/opt/google/chrome/cron/google-chrome
/opt/google/chrome/natives_blob.bin
/opt/google/chrome/google-chrome
/opt/google/chrome/xdg-settings
/opt/google/chrome/chrome_100_percent.pak
/opt/google/chrome/product_logo_16.png
/opt/google/chrome/nacl_helper
/opt/google/chrome/product_logo_24.png
/opt/google/chrome/chrome_200_percent.pak
/opt/google/chrome/icudtl.dat
/usr/bin/google-chrome-stable
/etc/cron.daily/google-chrome

```

---

### Post by Daveski17 on 2016-01-14
That's interesting thanks. I take it that with Chrome installed I type **dpkg-query --listfiles google-chrome-stable** into the Terminal and it lists these files. After uninstallation wouldn't these files all be removed?

---

### Post by deadflowr on 2016-01-14
> **Daveski17 said:**
> That's interesting thanks. I take it that with Chrome installed I type **dpkg-query --listfiles google-chrome-stable** into the Terminal and it lists these files. After uninstallation wouldn't these files all be removed?
Depends on how they are uninstalled.
If you where to run
**apt-get remove package**
then it'll uninstall the package but leave configuration files behind.
If you use
**apt-get purge package**
then it'll uninstall and remove any configuration files the package has.

---

### Post by Daveski17 on 2016-01-14
> **deadflowr said:**
> Depends on how they are uninstalled.
If you where to run
**apt-get remove package**
then it'll uninstall the package but leave configuration files behind.
If you use
**apt-get purge package**
then it'll uninstall and remove any configuration files the package has.

OK thanks.

---

### Post by vasa1 on 2016-01-14
I forgot to mention a bunch of ".desktop" files in /home/vasa1/.local/share/applications. I didn't bother to figure out whether this is because of Google Chrome or because I use Google Drive, Docs, etc even with Firefox.

And **locate google-chrome** is even more exhaustive. It picks up anything with "google-chrome" in it, even in your home folder. To ensure **locate** gives the latest picture, first run **sudo updatedb**.

---

### Post by Daveski17 on 2016-01-15
> **vasa1 said:**
> I forgot to mention a bunch of ".desktop" files in /home/vasa1/.local/share/applications. I didn't bother to figure out whether this is because of Google Chrome or because I use Google Drive, Docs, etc even with Firefox.

And **locate google-chrome** is even more exhaustive. It picks up anything with "google-chrome" in it, even in your home folder. To ensure **locate** gives the latest picture, first run **sudo updatedb**.

OK, thanks for the info.

---

