---
title: "Play BBC Radio problem"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by aaronfromchina on 2008-09-28
I would like to play BBC Radio on Firefox. It does not appear any problems on Ubuntu Gusty (7.10), but it does not work on Hardy(8.04).

Here is a screenshot of BBC player
[IMG]http://photo1.bababian.com/usr508492/upload13/20080929/sJu6w5EVqBQwury5XhjHTnPtUpeE1Tc545SEWCcSacMyr5yONuXrmqQ==.jpg[/IMG]

I was wondering if Firefox plugin is properly configured.
Here is a screenshot of Firefox plugin
[IMG]http://photo1.bababian.com/usr508492/upload13/20080929/sE7qYLE13mfiAdmj3nXziERfEPlNiZjQXNOr9rBzgK9g2QPpkPPDvEA==.jpg[/IMG]

---

### Post by skullmunky on 2008-09-29
the BBC player looks like Flash, and you have the Flash plugin installed, so that's good... does it show up at all, or just show up and no sound?

Do other flash sites (for example, YouTube) work ok?

---

### Post by aaronfromchina on 2008-09-29
YouTube works fine.

BBC radio player doesn't have sound.

---

### Post by ibizatunes on 2008-09-29
You need to install VLC mozzila plug in, its in the repo's

---

### Post by aaronfromchina on 2008-09-30
Thanks for you reply.

have a try.
apt-get install mozilla-plug-vlc
it still does not work.

I was thinking if I install too many plugins. I've tried disable some plugins, but haven't get it fixed. :(

---

### Post by _sAm_ on 2008-09-30
Install this plugin in Firefox: [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Run the wizard for it and try again.

Some sites didn't work for me before I changed to latest vlc on Ubuntu.

---

### Post by aaronfromchina on 2008-10-05
get the problem solved.
 
find the following code on ubuntu guide.

```

cd /usr/lib/firefox-addons/plugins
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

```

[IMG]http://photo1.bababian.com/usr508492/upload13/20081001/sZZI63cYN57a6nDb9Pcq11zR6lOS4FkQYDFl0mp7oAvWXh3pdEscYGQ==.jpg[/IMG]

---

