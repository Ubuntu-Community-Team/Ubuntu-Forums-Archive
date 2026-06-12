---
title: "Mozilla Mplayer Plugin"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by pitchdiesel on 2008-12-01
So I've installed the Mozilla Mplayer plugin and still Firefox keeps telling me to install Mplayer. Checking about: plugins, I see that it's not listed there.. I'm not sure of the format to install Mplayer to a specific dir, ~/.mozilla/plugin or if that would even be the fix. This happens with other plugins too! Is there a way for me to fix this issue permanently?

---

### Post by SunnyRabbiera on 2008-12-01
eh you may wish to install totem mozilla too, sometimes mplayer in mozilla doesnt work right.

---

### Post by gandaran on 2008-12-01
> **pitchdiesel said:**
> So I've installed the Mozilla Mplayer plugin and still Firefox keeps telling me to install Mplayer. Checking about: plugins, I see that it's not listed there.. I'm not sure of the format to install Mplayer to a specific dir, ~/.mozilla/plugin or if that would even be the fix. This happens with other plugins too! Is there a way for me to fix this issue permanently?
here's how it works
you can either install mplayer-plugin and remove totem-plugin, if you do this mplayer will be the default firefox plugin for every media file type
or you can have both plugins installed, totem will still be the default plugin for most media type files except some like real audio and video, if you go to a webpage with embeded real files it's mplayer that pops up, but you can change this behaviour, go to firefox » edit » preferences »  applications tab, now just specify which files mplayer or totem opens
you don't need to install mplayer to a specific directory, just open synaptic package manager, mark for install the **mozilla-mplayer** package and hit the apply button
also install the w32codecs package, install medibuntu repo to get them [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by m_l17 on 2008-12-02
Take a look at this thread if things still not working for you:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

