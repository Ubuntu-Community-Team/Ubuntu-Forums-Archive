---
title: "Problems with RealPlayer 11..."
date: 2008-10-14
forum: New to Ubuntu
---

### Post by ItecKid on 2008-10-14
So I installed the Real player 11 with the following code:

```
chmod 777 RealPlayer11GOLD.bin
```

and

```
./RealPlayer11GOLD.bin
```

However, I seem to be unable to start the program, and when I try to play music (by right-clicking on the track and selecting 'Open with Real Player 11') I get the following error:

```
KDEInit could not launch 'realplay'.:
Could not find 'realplay' executable.
```

Thoughts?  Or, is there another player that will run .wma files?

Or, better still, is it possible to run Ruckus through Wine?

---

### Post by milton1 on 2008-10-14
My first suspicion would be that the 'realplay' executable is in a location not pointed to in your $PATH variable. Start by making sure the executable is somewhere on your system.

```
sudo updatedb
locate realplay 
```

---

### Post by ItecKid on 2008-10-14
I did as you suggested, and the 'locate realplay' turned out the following:

```
locate realplay
/home/obriem5/.gnome/apps/realplay.desktop
/home/obriem5/.kde/share/applnk/realplay.desktop
/home/obriem5/.kde/share/icons/hicolor/16x16/apps/realplay.png
/home/obriem5/.kde/share/icons/hicolor/192x192/apps/realplay.png
/home/obriem5/.kde/share/icons/hicolor/32x32/apps/realplay.png
/home/obriem5/.kde/share/icons/hicolor/48x48/apps/realplay.png
/home/obriem5/.kde/share/mimelnk/application/vnd.rn-realplay.desktop
/home/obriem5/.local/share/applications/realplay.desktop
/home/obriem5/.local/share/icons/hicolor/16x16/apps/realplay.png
/home/obriem5/.local/share/icons/hicolor/192x192/apps/realplay.png
/home/obriem5/.local/share/icons/hicolor/32x32/apps/realplay.png
/home/obriem5/.local/share/icons/hicolor/48x48/apps/realplay.png
/home/obriem5/.local/share/locale/de/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/locale/es/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/locale/fr/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/locale/it/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/locale/ja/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/locale/ko/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/locale/pt_BR/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/locale/zh_CN/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/locale/zh_TW/LC_MESSAGES/realplay.mo
/home/obriem5/.local/share/mime/application/vnd.rn-realplay.xml
/home/obriem5/.local/share/mime/packages/realplay.xml
/home/obriem5/Downloads/RealPlayer/realplay
/home/obriem5/Downloads/RealPlayer/realplay.bin
/home/obriem5/Downloads/RealPlayer/postinst/profile.d/realplay.csh
/home/obriem5/Downloads/RealPlayer/postinst/profile.d/realplay.sh
/home/obriem5/Downloads/RealPlayer/share/realplay
/home/obriem5/Downloads/RealPlayer/share/realplay.applications
/home/obriem5/Downloads/RealPlayer/share/realplay.desktop
/home/obriem5/Downloads/RealPlayer/share/realplay.keys
/home/obriem5/Downloads/RealPlayer/share/realplay.mime
/home/obriem5/Downloads/RealPlayer/share/realplay.png
/home/obriem5/Downloads/RealPlayer/share/realplay.xml
/home/obriem5/Downloads/RealPlayer/share/icons/realplay_16x16.png
/home/obriem5/Downloads/RealPlayer/share/icons/realplay_192x192.png
/home/obriem5/Downloads/RealPlayer/share/icons/realplay_32x32.png
/home/obriem5/Downloads/RealPlayer/share/icons/realplay_48x48.png
/home/obriem5/Downloads/RealPlayer/share/realplay/embedded_logo.png
/home/obriem5/Downloads/RealPlayer/share/realplay/icon.png
/home/obriem5/Downloads/RealPlayer/share/realplay/logo.png
/home/obriem5/Downloads/RealPlayer/share/realplay/playlist_error.png
/home/obriem5/Downloads/RealPlayer/share/realplay/prefs_general.png
/home/obriem5/Downloads/RealPlayer/share/realplay/setup_title.png
/home/obriem5/Downloads/RealPlayer/share/realplay/setup_welcome.png
/usr/share/icons/crystalsvg/16x16/apps/realplayer.png
/usr/share/icons/crystalsvg/32x32/apps/realplayer.png
/var/tmp/kdecache-obriem5/http/i/images.real.com_pics_ebi_linux_button_download_realplayer.gif_23b2d44c
```

---

### Post by ooobuntooo on 2008-10-14
chmod a+x RealPlayer10GOLD.bin

then drag RealPlayer10GOLD.bin into the terminal and press enter

---

### Post by ItecKid on 2008-10-14
Thank you very much, I am able to start the program now, that is a step in the right direction!

However, when I attempt to play my music, though the volume slider is all the way up and not muted, there is no audio...

---

