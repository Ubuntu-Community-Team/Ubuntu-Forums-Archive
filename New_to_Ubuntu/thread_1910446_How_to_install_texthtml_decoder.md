---
title: "How to install text/html decoder"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by Catlike on 2012-01-17
I am taking an on-line class which has videos to watch. Just started it. When I click the link to the video, the message pops up which says "Need text/html decoder. The package with this plugin is not installed".
I did not find anything matching the surficial description above in the Ubuntu software center.
How can I find and install the required text/html decoder?
Thank you.

---

### Post by mcduck on 2012-01-17
Your web browser is a text/html decoder. I'd assume the link is constructed in some non-standard (or the server configurations aren't correct) way if you get such error. The server is supposed to send you a video file but sends a web page instead, which the video player f course can't open.


..or perhaps the link isn't actually to a video file, but a playlist instead? In that case you need a video player that handles playlists? Mplayer might work if the default player doesn't.

---

### Post by Catlike on 2012-01-17
Thanks. Just installed GNOME MPlayer; hope this works!

---

