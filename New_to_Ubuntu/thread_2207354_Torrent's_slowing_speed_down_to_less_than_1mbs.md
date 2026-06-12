---
title: "Torrent's slowing speed down to less than 1mbs"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by david98 on 2014-02-23
Here is the problem I have every torrent file I download reduces my web browser to a virtual halt ie taking 5 min to open a webpage. I know it's got nothing to do with my net speed because I do test's regularly and get between 18-26 mb's so what is the problem surely my system can download 1 torrent at around 1.5mbs and use my browser. I never had this problem before when I was using the same OS saucy salamander same laptop only thing that's changed is my hdd. As you can imagine this is extremely annoying. Any help with this matter would be greatly appreciated.

Thank's in advance

---

### Post by kostkon on 2014-02-23
Try to reduce the max number of connections that your torrent client can make and also you could set a max download limit, in its preferences.

If you mean 18-26 Mbit/s, then your download speed varies between 1.8 and 2.6 MB/s, which means that your torrent downloads could be stealing all your available bandwidth, that's why it would be better if you could set a max download speed limit for your torrents, for example set it to 1MB/s.

Hope that helps.

---

### Post by david98 on 2014-02-23
I mean 18 mbs to 26mbs not 1.8-2.6 Iv'e already set my download speed for torrent's to 1.5 and I try to limit to only 1 torrent. I will try limiting it to 1mbs to see if it help's but I doubt it will. It use to run perfectly with same ISP all I done was changed my hdd and fresh install now it seems I can either download torrent's or surf the net which cant be right. I pay a little extra for my broadband so as to get super fast fibre but at the moment it's useless for my needs.

---

### Post by david98 on 2014-02-23
Solved just removed transmission-gtk then reinstalled it now everything seem's to be working fine.

---

