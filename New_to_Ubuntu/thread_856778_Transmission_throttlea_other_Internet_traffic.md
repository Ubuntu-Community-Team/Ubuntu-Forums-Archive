---
title: "Transmission throttlea other Internet traffic"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Djalmahal on 2008-07-11
when I run Transmission, even though I set the max download upload to low (10KB/s), Firefox runs much slower, ordinary download fail, webpages load sometimes not. The Transmission use of say 10KB/s doesn't explain that alone, my total bandwidth is 50KB/s. Is this a problem with Transmission, some other setting or does my Internet Provider throttle my bandwidth due to torrent use?

Any advice?

Andreas

---

### Post by Bakon Jarser on 2008-07-11
Try another bittorrent client and see if the problem goes away.  Try Deluge.

---

### Post by Yuki_Nagato on 2008-07-11
Torrents work on two fronts.  You are both downloading what you do not have and uploading what you do have.  Download speed is not your problem.  Uploading KILLS American bandwidth.  You must set your upload speed much lower.  I find that 5 - 10 KB will not affect anything else.

But please remember: it is polite to upload as much as you have downloaded.

---

### Post by Djalmahal on 2008-07-11
I changed to deluge and the problem seems to be solved. I already throttled the upload speed in transmission to 5kb/s so that was not the problem.

Sometimes a simple solution just works ;-)

Thanks
Andreas

---

