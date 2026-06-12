---
title: "no sound with media player"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by Unguidedone on 2013-01-15
I have been using ubuntu 12.04 for 4 months now and i did a really stupid thing today.  On the software update it said that it could not install all updates and needed a partial system update.  So i clicked upgrade and it removed vlc player.  I was using vlc player because it was the only media player that played sound.

so vlc is gone and when i try to play mp4's media player comes up and it has no sound.

i tryed to reinstall vlc and got this error:
The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.5+git20130114+r499-0~r42~precise1) but 2.0.5+git20130114+r499-0~r42~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.4ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.4ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.3 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.3 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.3 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed



it also says im missing lib6 but when i checked if it was installed it was there.

---

### Post by Unguidedone on 2013-01-15
ok ok
installed all missing packages for vlc player

/me pats self on back

but gstreamers are still hopelessly screwed up

i could use some help still because vlc might work fine now but there is still no sound in "media player, dragon player, gnome player"  while rythombox still works | odd yes because dosent it use gstreamers too?

so ah someone please replay back this is quite one sided

---

