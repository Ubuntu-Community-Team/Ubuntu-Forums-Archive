---
title: "[SOLVED] internet problem"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by pasargad on 2008-06-18
hello it's me again :)
i use transmission to download a torrent link,but when i downloading. i can not surf the web,i can not open any page.what's the problem:confused:

---

### Post by ice60 on 2008-06-18
maybe the browser is timing out because transmission is hogging all your bandwidth. it's just a guess, has transmission got a  Speed Limit Mode where you can tell it to slow down a bit so there's some bandwidth for your browser?

EDIT: i found a picture that shows where you can limit the speed, that's if the linux version looks like that?

---

### Post by azurepancake on 2008-06-18
The only thing I can recommend is perhaps capping your upload speed, like ice60 recommended. Visit a speed testing website, such as [Speakeasy]("http://www.speakeasy.net/speedtest/") and divide the upload speed by 8 to get the KB/s (Speakeasy does the math for you, the KB/s are displayed just below the speed gauges after the test).

Then set the upload speed to %80 of your KB/s.

You can also try another bit torrent client. There are plenty of excellent torrent clients out there for Linux. I use Deluge for example, which is a very powerful client that still remains light weight. If you decide to give it a shot, I recommend downloading the .deb package from there website. Last time I checked, the Deluge in the Ubuntu repositories was out-dated.

---

### Post by cariboo on 2008-06-18
You can limit upload and download speeds in Transmission by going to Edit-->Preferences

Jim

---

### Post by pasargad on 2008-06-19
thanks it's work i change the download limit from 100 to 80 kbp/s :) thank to everyone..

---

