---
title: "How to automatically exit rtorrent after completing a download ?"
date: 2014-10-26
forum: New to Ubuntu
---

### Post by rjochacko on 2014-10-26
Help me to fix this problem.
My intention is to execute another command after rtorrent shows "done" message. For example I want to run: 
rtorrent example1.torrent ; wget example2.mp4

But after finished with rtorrent it doesn't kill the rtorrent so the next command never execute unless I press ^q manually.

I am using rTorrent 0.9.4/0.13.4 in ubuntu 14.04.

---

### Post by nerdtron on 2014-10-26
Should the rtorrent download finish first before you execute the next command?
Or you just need to run the second command after you issued the rtorrent download command? (like they will download simultaneously)

---

