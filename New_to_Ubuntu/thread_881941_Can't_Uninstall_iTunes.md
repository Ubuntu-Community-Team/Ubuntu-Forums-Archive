---
title: "Can't Uninstall iTunes"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by jcway212 on 2008-08-06
This might have been asked before, I couldn't find it after doing a search (the forum search feature is not the best, I use Google to search these forums.) Anyways, I install iTunes via Wine and for some reason I am not able to uninstall it.

ERROR THAT I AM GETTING:

The uninstall process starts and it freezes at 
Status : Starting services
File: CDDBControlApple.dll, folder: C:\Program Files


I can get a screenshot when I get off work.

---

### Post by NewJack on 2008-08-06
What version of WINE do you have and what version of ITunes are you looking to install?

This link shows how WINE 1.1.1 works with ITunes 7.7:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12953&iTestingId=28981](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12953&iTestingId=28981)

Here is a link detailing how ITunes 7.3 installed in WINE:
[http://www.wine-reviews.net/applications/itunes-73-on-linux-with-wine.html](http://www.wine-reviews.net/applications/itunes-73-on-linux-with-wine.html)

I haven't tried any of this personally, since I have a macbook from work that I use to sync my iPhone to currently.

Hopefully those links helped.

Joe

---

### Post by SuperSonic4 on 2008-08-06
have you tried looking in /home/<user>/.wine and looking for the iTunes folder or something. If you find it try deleting that.

I use Amarok to sync my ipod with

---

### Post by NewJack on 2008-08-06
> **SuperSonic4 said:**
> have you tried looking in /home/<user>/.wine and looking for the iTunes folder or something. If you find it try deleting that.

I use Amarok to sync my ipod with

The only problem is that he might have DRM'ed music from ITunes in his library.

@jcway- I just found this article on MacOSXhints.com

[http://www.macosxhints.com/article.php?story=20070130165510807](http://www.macosxhints.com/article.php?story=20070130165510807)

Maybe that will help you with your music library once you get things set up.

Joe

---

### Post by jcway212 on 2008-08-06
WOW! 3 Great responses!!! Kudos to all of you! Anyways, I will let you know the outcome of those posts when I get back home. Thanks!

---

### Post by billgoldberg on 2008-08-06
removing wine would do the trick :p

You can play itunes drm crap with eltunes (google it, look for the torrent) and there are numerous syncing apps.

---

