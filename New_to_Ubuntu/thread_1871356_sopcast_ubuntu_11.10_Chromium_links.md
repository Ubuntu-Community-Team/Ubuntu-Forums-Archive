---
title: "sopcast ubuntu 11.10 Chromium links"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by sssuizaaa on 2011-10-28
Hello,

I installed sopcast in ubuntu 11.10 following the instructions I found for instance here:
[http://ubuntuforums.org/showthread.php?t=1609505&highlight=sopcast+gui](http://ubuntuforums.org/showthread.php?t=1609505&highlight=sopcast+gui)
or here:
[http://www.ryukent.co.uk/2010/10/howto-set-up-sopcast-in-ubuntu-10-10-including-chromium-sop-links/](http://www.ryukent.co.uk/2010/10/howto-set-up-sopcast-in-ubuntu-10-10-including-chromium-sop-links/)
which are the same and basically involve doing this after the installation of sopcast:
gconftool-2 –set –type=string /desktop/gnome/url-handlers/sop/command ‘sopcast-player “%s”‘
gconftool-2 –set –type=bool /desktop/gnome/url-handlers/sop/enabled true
gconftool-2 –set –type=bool /desktop/gnome/url-handlers/sop/need-terminal false
That does not work for me. I'm using Chromium 14.0.835.202 but when I click in a sop link the message I get from chromium is the image attached which I guess is not what I want.
There seems to be something not working properly with the gconftool commands but I do not know what that can be.
I managed to make the links work with Firefox following this:
[http://maketecheasier.com/install-sopcast-ubuntu/2010/06/10](http://maketecheasier.com/install-sopcast-ubuntu/2010/06/10)
but I do not know what happens with Chromium.

Any ideas?

Thank you very much,

Sssuizaaa

---

### Post by sssuizaaa on 2011-11-01
Nobody?

Thank you

---

### Post by Johanu on 2012-04-22
I've managed to make it work with Chrome 18.0.1025.162 and Ubuntu 11.10, so I hope this is useful to you.

You have to add a sopcast-player.desktop file inside ~/.local/share/applications configured in this manner:

```
[Desktop Entry]
Name=Sopcast Player
Exec=sopcast-player %u
Icon=sopcast.icon
Type=Application
Terminal=false
MimeType=x-scheme-handler/sop;
```

Then, you have to configure mimeapps.list and add the sopcast-player.desktop to your Added Associations. Like this:

```
[Added Associations]
x-scheme-handler/sop=sopcast-player.desktop;
```

After that all should be working. When you press a sop:// link in Chrome/Chromium it should launch the sopcast player and start connecting to the channel.

---

