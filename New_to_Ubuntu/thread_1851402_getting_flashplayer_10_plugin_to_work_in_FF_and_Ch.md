---
title: "getting flashplayer 10 plugin to work in FF and Chromium"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by GiancarloG on 2011-09-28
Hello All, am new on here with a problem that I hope someone - anyone - can help me with.  I am happily using Ubuntu 10.04 LTS but now have been forced to update the flash player plugin for both Firefox and Chromium browsers ("run this time" does not work).  OK, I followed the instructions to download, extracted the respective .so file (libflashplayer.so) and copied it to the plugin folders for the browsers eg /usr/lib/mozilla/plugins (via terminal)  Everything seemed fine including seeing the new .so file (updated 19 Sep) in the relevant folder (presume has overwritten the old one of same name, dated Feb 2011), so I closed the browsers and re-started them in turn.  However, to my dismay, in both cases the old version 9 plugin is still the one recognised, and hence I can't play flash files in either browser.  I have retraced my steps but ended up in the same place, the browsers don't want to update the plugin (or are these applications looking for plugins in different folders, how can I check this?).  I also have Gnash and swfdec flash players installed but how can they help the problem?  Is there a general problem with new Flash support for the browsers on Linux?  Should I download latest versions of the browsers?

---

### Post by bokgeneraal on 2011-09-28
Firefox has a add-on called "flash aid" that is supposed to install the correct flash plugin for you.

---

### Post by MG&amp;TL on 2011-09-28
I might be misinterpreting the question, but wouldn't:

```
sudo apt-get install ubuntu-restricted-extras
```

do?

---

### Post by fooman on 2011-09-28
> **bokgeneraal said:**
> Firefox has a add-on called "flash aid" that is supposed to install the correct flash plugin for you.

+1

that particular add-on was created by one of our members here (lovinglinux) and it works great!

it will remove any un-needed flash related items (gnash etc...) and install the correct flash for your system.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

after installing....it will work for chrome as well.  :)

---

