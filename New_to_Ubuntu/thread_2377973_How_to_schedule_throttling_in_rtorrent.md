---
title: "How to schedule throttling in rtorrent"
date: 2017-11-18
forum: New to Ubuntu
---

### Post by bomberb17 on 2017-11-18
Hello, I'm using rtorrent and I'd like to set up the rtorrent.rc configuration file to throttle the upload speed during the day. Is this the way to do it? I could not find any example online

 	 		 			 			 				```
schedule = throttle_1,16:00:00,24:00:00,upload_rate=30
schedule = throttle_2,21:00:00,24:00:00,upload_rate=65
```

---

### Post by Holger_Gehrke on 2017-11-18
[Here's a link to the right place in the Manual on the rtorrent-wiki on github]("https://github.com/rakshasa/rtorrent/wiki/Common-Tasks-in-rTorrent#scheduling-download-rate")

Holger

---

### Post by bomberb17 on 2017-11-18
Thank you, will try it out and see if it works

---

### Post by bomberb17 on 2017-12-04
Works just fine, thanks!

---

