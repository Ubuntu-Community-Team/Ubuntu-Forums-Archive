---
title: "General Audio problems04"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by scott42 on 2014-04-12
Hi All:
Brand new user, and I have some issues with audio. I am using Chromium and Ubuntu 12.04 LTS. What do I need to do to get audio to play? For example from a site like tune-in.com? If I click on a stream to play, it shows a couple of pop ups requesting permission to use windows media player and quicktime, which I allow, but the stream doesn't play. Also, if I try to enter a URL in the default player, it doesn't play. I'm sure it's something fairly simple, but haven't been able to figure it out yet!

Thanks for any assistance

---

### Post by gordintoronto on 2014-04-12
You may need to install the "restricted extras."

---

### Post by monkeybrain20122 on 2014-04-12
Windows player and quicktime don't work in Linux. You need the codecs and the player plugins that can play these formats but without actually needing quicktime or Windows media player. As Gord said install ubuntu-restricted-extras for the codecs. For the player the totem plugins are already installed by default, but in my experience they are not that good. So if it still doesn't work for you install gecko-mediaplayer from the repository and then go to Firefox-addon and set all Totem plugins (they are associated with the name "Videos") to "never activated" and restart Firefox, now gecko-mediaplayer will take over.

---

