---
title: "Messenger For Ubuntu"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by Saloumi on 2012-01-20
I recently downloaded Messenger but everytime i click on the open with wine browser button, nothing happens !!!! Should I download it again but this time from a specific site or what on earth should i do ???










                         Answer soon, 
                                              Saloumi

---

### Post by Grenage on 2012-01-20
Consider a native alternative, such as empathy or pidgin.

---

### Post by _0R10N on 2012-01-20
Try executing it from a terminal and see whether there's an error message displayed when trying to run the app.

---

### Post by saneearth on 2012-01-20
Not sure which "Messenger" program for which you are referring, but there are several Linux clients that work great. Been around for a while and never heard that anyone was using a windows version of a messinger through wine, or maybe I did hear something long ago, but I would try a native client first.

---

### Post by fantab on 2012-01-20
> **Saloumi said:**
> I recently downloaded Messenger but everytime i click on the open with wine browser button, nothing happens !!!! Should I download it again but this time from a specific site or what on earth should i do ???

USE **PIDGIN** for Linux. It is better than Messenger IMO.

---

### Post by goofey24 on 2012-01-20
> **saneearth said:**
> Not sure which "Messenger" program for which you are referring, but there are several Linux clients that work great. Been around for a while and never heard that anyone was using a windows version of a messinger through wine, or maybe I did hear something long ago, but I would try a native client first.

I used AIM via WINE quite awhile back. But only a way to old version would work :(

---

### Post by Bölvaður on 2012-01-20
I assume that by "messenger" you actually mean MSN Live Messenger
I also assume that you do not want any native alternative (pidgin, aMSN...) and only want what you are trying to run.

I dont like guessing and assuming what people actually mean when they say something when Im helping them. But this is probably the link you are looking for: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=127](http://appdb.winehq.org/objectManager.php?sClass=application&iId=127)

As you can see for the 8.1 version there is a how-to

> [IMG]http://appdb.winehq.org/images/blank.gif[/IMG]                  HOWTO  I got as far as the login screen doing the following               
  
[LIST]
[*]Install MSN (important)
[*]Download Winetricks                                    
      wget [http://www.kegel.com/wine/](http://www.kegel.com/wine/)**winetricks**
[*]Now using winetricks install riched20, msxml3 and gdiplus                            
      sh winetricks riched20 gdiplus msxml3 flash
[*]Set Windows version to Windows 2000
[*]Now you can start MSN Messenger
[/LIST]



You can go to the wine subforum on the ubuntuforums and ask there... I would think people there would be way more helpful than the very helpful people here on the absolute beginner subforum.

---

