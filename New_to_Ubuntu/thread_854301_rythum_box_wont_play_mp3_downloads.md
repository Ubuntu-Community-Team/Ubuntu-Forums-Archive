---
title: "rythum box wont play mp3 downloads"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by workshop1702 on 2008-07-09
hi just dowloaded a couple of mp3 audio files rythm box wont play them. anyone got any ideas , it say couldnt start playback (null). dont have a clue how to fix this anyone got any ideas please.:confused:

---

### Post by konungursvia on 2008-07-09
If you download and install gstreamer and its plugins, it should fix the problem even for rythm box. Do this: ```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly mpg123
``` in the Terminal shell, hit enter, and enter your password when it says to.

---

### Post by chetan.89 on 2008-07-09
Try Amarok or install the gstream plugin for totem. That should do.

Cheers.

---

### Post by workshop1702 on 2008-07-09
tried downloading all the gstreamer codecs still wont work

---

### Post by chrisod on 2008-07-09
Are you sure they are good files? Can Rythmbox play any other MP3 files that you have available>

---

### Post by stchman on 2008-07-09
You may have corrupt mp3 files.  Does your system play mp3s right now?

---

