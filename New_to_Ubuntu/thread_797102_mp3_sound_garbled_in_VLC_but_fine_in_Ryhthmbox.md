---
title: "mp3 sound garbled in VLC but fine in Ryhthmbox"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by johanus on 2008-05-17
I upgraded 7.10 to 8.04.  I now find that playing an mp3 with VLC produces a distinctly garbled ("underwater") sound.  The same mp3 plays fine with MPlayer or Rhythmbox, but both VLC and Movie Player produce the same garbled output. What might account for this and how can I attempt a fix? Uninstalling and reinstalling VLC did not help

---

### Post by mc4man on 2008-05-17
The default for audio module is generally autodetect so the first thing to try is go to preferences -> sound and change music and movies from auto detect to alsa. You can also make that change in vlc from settings -> prefs -> audio -> output module (first enable advanced options)

---

### Post by johanus on 2008-05-17
> **mc4man said:**
> The default for audio module is generally autodetect so the first thing to try is go to preferences -> sound and change music and movies from auto detect to alsa. You can also make that change in vlc from settings -> prefs -> audio -> output module (first enable advanced options)

Thanks.  Made those changes but still see the same distortion in the two apps, good sound in the other two. I prefer VLC and would like to get it to work; it performed fine before the upgrade.

---

