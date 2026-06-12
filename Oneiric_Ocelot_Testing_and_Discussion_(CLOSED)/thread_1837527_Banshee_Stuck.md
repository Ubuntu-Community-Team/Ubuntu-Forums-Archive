---
title: "Banshee Stuck"
date: 2011-09-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by thonuz on 2011-09-01
Banshee player not playing songs

Also it will not change songs forcing you to kill or logout.
I am using now gmusic browser to play songs but banshee is broke. You cant even see the program in xubuntu. 
I can't tell about unity cause it suks but in gnome-shell its same.
It freezes up. Is this because of unity dependent files?

---

### Post by SoFl W on 2011-09-01
I have noticed Banshee has not been able to play music lately.  If you delete the folder

```
/home/YOUR_USER_NAME/.config/banshee-1
```It fixes the problem... until you exit and restart the program.  It also has to rebuild the database once you do this.  I moved back to Rhythmbox for now.

---

### Post by MacUntu on 2011-09-02
Banshee has been acting up over the last couple of weeks here as well. I tried to rebuild my database but that didn't change a thing. Let's find out if there are bug reports about it - there's still a good months to fix stuff. :)

---

### Post by P-I H on 2011-09-02
Banshee is working OK in my just installed and fully updated beta1 with amd64.
It worked fine to change the music library to my music archive on an Ubuntu Server. Banshee's music library updated OK, both albums and album art, with the "Rescan music libary" tool.
Flac played directly, but to play mp3 I installed both gstreamer0.10-ffmpeg and gstreamer0.10-fluendo-mp3. It might be enough to install only the gstreamer0.10-fluendo-mp3. It didn't work in my case but I tried without to restart Banshee.

---

