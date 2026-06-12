---
title: "Installed Chrome, cannot access Adobe Flash Global Privacy Panel"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-11
I just installed Chrome and I cannot access the Adobe Flash Global Privacy Panel on Kubuntu 14.04. I thought downloading Chrome meant I would get Adobe Flash as well. When I went to ([https://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html](https://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html)), It says I need to install Flash and I don't see the Global Privacy Panel where I can change Flash settings. Do I have to install Flash manually? If so, how? Thanks.

---

### Post by deadflowr on 2014-09-11
Yes you do have flash.
It is , however, not a version that is normal, which is probably the reason it isn't listed as installed on adobe's site.
(Bug?, Possibly)
Chrome uses what is known as the pepper plugin api(ppapi) as opposed to the old, and more common, netscape plugin api (npapi)
Which might have something to do with it not working right on that site... 
However,
You should be able to access the content control panel by Right clicking on any flashplayer window, though.

---

### Post by garycheng12 on 2014-09-11
Thank you, was able to access settings through that.

---

### Post by garycheng12 on 2014-09-11
I just found out that accessing that link to go to Adobe global settings did not work when I used [https://,](https://,) only when I used http:// did it work. Would be helpful to know why, as I use HTTPS Everywhere extension for Chrome and this problem may be prevalent in other sites.

---

