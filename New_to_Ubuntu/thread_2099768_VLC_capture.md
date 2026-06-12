---
title: "VLC capture?"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-30
How can one capture a video song of a movie played on vlc player?

Thanks.

---

### Post by gnush on 2012-12-30
Do you want to extract the audio from the movie? If so, I don't know if you can do it with VLC, but you can do it with mplayer.

```
$ mplayer -dumpaudio -dumpfile audio.mp3 movie.avi
```

---

### Post by Yezinki on 2012-12-30
Thanks gnush for replying.

I want to extract/capture both audio, video of the song.

---

### Post by gnush on 2012-12-30
Ah, you want to cut out a certain part of a movie? Then I guess you could use avidemux.

---

### Post by davdo2004 on 2012-12-30
> **Yezinki said:**
> How can one capture a video song of a movie played on vlc player?

Thanks.

If you click on the 'view' tab on vlc and then tick 'advanced controls' you will now see a record button on the player.

---

### Post by coldcritter64 on 2012-12-30
> **Yezinki said:**
> Thanks gnush for replying.

I want to extract/capture both audio, video of the song.
+1 Avidemux, may be worth a check for you. You can save video or audio tracks separately from the menu options.

---

### Post by andrew.46 on 2012-12-30
The most basic way to accomplish this is to use the video/audio capture tool native to vlc. Go to View --> Advanced Controls and you will see the 'Record' button, I have attached a screenshot to show this exactly. Hope this is what you are after?

---

### Post by Yezinki on 2012-12-30
Thanks andrew.46.

Where is the flv file saved?

---

### Post by andrew.46 on 2012-12-30
> **Yezinki said:**
> Where is the flv file saved?

I am not sure where the *default* location is (perhaps $HOME) but you can certainly decide for yourself where to place the resulting files by placing a location in Tools --> Preferences --> Input & Codecs --> Files --> Record Directory or Filename and browse for a suitable place.

Bear in mind there are many other methods to accomplish the same end but certainly this is the quickest and certainly achieves reasonable results.

---

