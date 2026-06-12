---
title: "how to get aria2c download from 2 torrent files?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-10-29
I have same torrent in 2 files how do I have aria2 download from them both? Both files are in the same dir on the computer. Is the below how I do it? Also is their a gui for this program?

user@home:~/Desktop$ ls
1.torrent 2.torrent
user@home:~/Desktop$ aria2c --bt-request-peer-speed-limit=50M --human-readable=true --min-split-size=50M --max-connection-per-server=2 --split=N -T 1.torrent 2.torrent

---

