---
title: "GMPC Tag Browser issue"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by D.Sync on 2008-06-05
I had recently created a tag string 'Browse by Album' under the Tag Browser column. When I double click on a song in an album, upon finish playback the song just stop. When I click next it displayed as 'Not Playing'. 

Is GMPC only able to play tracks according to the playlist? Can't I just playback songs using the Tag Browser custom setting?

---

### Post by Baelus on 2008-06-05
GMPC is a frontend for the MPD (Music Player Daemon) music server. MPD uses the 'Current Playlist' to tell it what to play.

By double clicking a song on the album you're adding that song to the Current Playlist. MPD reads that, plays the song and then sits there quietly.

So, yeah. You're right. GMPC can only play tracks according to the playlist. It's tied to how MPD works.

You can right click on the album and choose 'Add' to append the album to the bottom of the playlist, or you can choose 'Replace' to clear the playlist and just play that album.

- B

---

