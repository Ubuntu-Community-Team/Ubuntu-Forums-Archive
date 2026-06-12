---
title: "Is there any torrent client that downloads files in order?"
date: 2015-03-13
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-03-13
Hello guys 
I would like to know is there any bit-torrent client that support this feature, for example I have a TV series torrent which contain 20 files (episodes) as a total and I would like my torrent client to download the files (episodes) in order episode 1 then episode 2 automatically.

---

### Post by ian-weisser on 2015-03-13
In some, like Deluge, you can set the priority of some files/chunks. But in order? No.

Being super-specific like that will increase your download time. Clients generally download what the swarm offers and when the swarm offers it. If parts of 'episode 2' are not offered for a few seconds/minutes, you're telling the client to idle (download nothing) until it becomes available.

A workaround is to ONLY download 'episode 2' files from the swarm, then only download 'episode 3' files. You can easily do that manually, both Deluge and Transmission have the feature. But your total download time may be much greater than if you simply let the client work as designed.

---

