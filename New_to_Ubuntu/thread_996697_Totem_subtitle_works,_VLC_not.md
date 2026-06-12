---
title: "Totem subtitle works, VLC not"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by akkad on 2008-11-29
i have a movie and .srt subtitle, the subtitle is working properly on Totem player but with VLC is not, i believe it is about font issue because the font am using is arabic, where when i change the font in VLC the font shape still the same so this means the font didnt get changed, does this means that VLC has no read access to file or it is something else ??

the font am using is under this directory : /usr/share/fonts/truetype/ttf-arabeyes/ae_AlMateen-Bold.ttf, Totem is accessing it with no problem where VLC is not, so are there any permission modifications needed??

---

### Post by Xiong Chiamiov on 2008-11-29
VLC won't play subtitles automatically; have you turned them on (video -> subtitles)?

---

### Post by akkad on 2008-11-29
yes i did, in fact the subtitle appears on the screen, look, arabic words has a linkage between each character, just like when people write joined english characters, so to let this behaviour work we should use an arabic font, but the problem that whenever i change the font to the arabic font, vlc is not changing it and still using the default font(say sans for example), so sans will not show the subtitle correctly with joined-characters-words instead it will show them separate where it will be hard to read for arabic readers.

so it is about that vlc is not changing to the font i set.

---

