---
title: "Burning DVD with Brasero..."
date: 2019-06-12
forum: New to Ubuntu
---

### Post by Innernet on 2019-06-12
Hi.
Downloaded a movie using ClipGrab; worked well, got saved as .mp4, able to play the downloaded file.
When tried to burn to a DVD, converting process was requested.  Did it with VLC media player into one of the choices I guessed/chosed : to 720p for TV 'format'  as intention to play on a standalone DVD player. Seems it almost went well, I was able to play the saved conversion file that also used the .mp4 extension but audio plays off sync like 5 seconds before video.

Burning the DVD with Brasero, process starts burning the checksum, then burning the data and after like ~20 minutes, message of "100% burning complete" shows finalizing... then, started again to burn a 'second checksum'.  Seen that before.  
Eight ! hours later, not finished by the typical eject of the disc. Stuck somewhere at less that a 1/4 progress bar, doing nothing.  Turned laptop off.

Power cycled; got message of laptop was shut down from thermal protection but working fine 'now'

What is going on ?  What is the correct 'conversion' that should have been chosen ?  What is that endless, slow 'second' checksum burning ?  Burned DVD does not play.:(

---

### Post by CatKiller on 2019-06-12
> **Innernet said:**
> I guessed/chosed : to 720p for TV 'format'  as intention to play on a standalone DVD player.
... 
Burned DVD does not play.:(
I can't say anything about your burning issues, but your resolution was *way* too high. DVDs are MPEG-2 video at 720×576, for PAL, or 720×480, for NTSC. There is also a specific directory structure that must be used.

---

### Post by him610 on 2019-06-13
Try using xfburn instead.

---

