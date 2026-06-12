---
title: "HOWTO:  Using Mediasite on Linux"
date: 2009-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by MyR on 2009-04-04
My school uses a mediasite server powered by silverlight from microsoft to stream videos to the students.  I got it to work with the firefox moonlight plugin and a manual adjustment to the url.  These instructions should work for any flavor of Linux.  I tested this using moonlight 1.0.1 and firefox 3.0.8

Instructions:
1. Download the latest moonlight plugin from [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)
2. Install the plugin in firefox.  Click "file" then "open file".  navigate to the plugin you downloaded, select it, and click open.  Then click install.  Restart firefox as directed.
3. When you go to a mediasite link it must end with &playerType=sl1
for example: [http://mediasite.***.edu/?peid=ab4bbdb&playerType=sl1](http://mediasite.***.edu/?peid=ab4bbdb&playerType=sl1)

peace

---

### Post by agusdon on 2009-12-06
That worked for me too, but do you know how to play mediasite presentations in 2x with ubuntu?

---

### Post by bcooperb on 2010-04-20
Looks like the newer player for mediasite doesn't work with moonlight.... Some areas have a "classic player" option which seems to play some features. Can anyone else confirm this?

---

### Post by p_rynhart on 2010-06-20
Yes - we have both the new "Silverlight" version of the player along with the classic version available within our organisation.  I can confirm that the "Silverlight" version of the site does not appear to work (at least with Lucid - I just get a white screen in Firefox) whereas the classic version does work correctly.

Thanks,

Patrick

---

