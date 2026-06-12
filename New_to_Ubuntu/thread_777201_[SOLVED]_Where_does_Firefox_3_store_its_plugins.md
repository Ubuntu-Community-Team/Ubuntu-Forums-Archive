---
title: "[SOLVED] Where does Firefox 3 store its plugins?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Theo148 on 2008-05-01
I can't seem to find the folder where the Firefox 3 package keeps all its plugins. For Firefox 2 in Gutsy, it was under /usr/lib/firefox/plugins, but they don't seem to be there anymore. Does anybody know where they are kept now?

---

### Post by Nepherte on 2008-05-01
Even for Firefox 2 they're stored in ~/.mozilla/firefox

---

### Post by Theo148 on 2008-05-02
I can see the profile folders there, but I don't see any plugin files.

---

### Post by Xiong Chiamiov on 2008-05-02
Mine are in /usr/lib/firefox/plugins, but I also have an empty /usr/lib/firefox-3.0b5/plugins folder.

---

### Post by Theo148 on 2008-05-02
Well for me the only plugin in that folder is Flash player (from ubuntu-restricted-extras). I'm trying to find all the other plugins so that I can link them to my installation of Minefield.

---

### Post by nowshining on 2008-05-03
/home/username/.mozilla/plugins/

---

### Post by Theo148 on 2008-05-03
Er... that folder doesn't seem to exist.

---

### Post by nowshining on 2008-05-03
hmmm, did you try gonig into the profile folders and looking for a plugins folder?

---

### Post by Theo148 on 2008-05-03
I've checked all the profile folders, and there do not appear to be any plugin folders there... I wonder why the method of storing plugins was changed in Hardy?

---

### Post by gandaran on 2008-05-03
> **Theo148 said:**
> I've checked all the profile folders, and there do not appear to be any plugin folders there... I wonder why the method of storing plugins was changed in Hardy?

no, it's still the same, the plugins folder for firefox is /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins and sometimes depending on the plugin /usr/lib/mozilla-firefox.
you can also find a plugins folder in /home/user/.mozilla if you happen to have a plugin installed there.
actually what plugin you looking for?

---

### Post by Theo148 on 2008-05-03
I'm trying to find the media plugins (for all the different video formats and whatnot) that are installed by default with the Ubuntu version of FF3, so that I can link them to my installation of Minefield.

---

### Post by gandaran on 2008-05-03
> **Theo148 said:**
> I'm trying to find the media plugins (for all the different video formats and whatnot) that are installed by default with the Ubuntu version of FF3, so that I can link them to my installation of Minefield.

well, this depends on the media plugins you looking for, mplayer and xine plugins you will find them in the usual firefox/mozilla plugins folder's,vlc I don't know as I have never used it, gstreamer/totem is some thing else, they have they own plugins folder, look in /usr/lib/totem.

---

### Post by Theo148 on 2008-05-04
Ah, so that's where they are. :) Thanks for the help, I now have the totem plugins up and running in Minefield.

---

### Post by egozcl on 2008-05-21
/usr/lib/firefox-3.0b5/plugins

---

### Post by Theo148 on 2008-05-22
Okay, I did a little digging and I've found the new locations of all the FF3 plugins in Hardy:

For Shockwave Flash (if it's installed) - /usr/lib/firefox/plugins/
For all the Totem plugins - /usr/lib/totem/gstreamer/
For the gcj Java plugin - /usr/lib/jvm/java-6-openjdk/jre/lib/i386/gcjwebplugin.so
For the iTunes detection plugin - /usr/lib/xulrunner-1.9b5/plugins/librhythmbox-itms-detection-plugin.so

I guess I can call this thread solved now (and I just realised that the 'mark thread as solved' feature is back :P ).

---

