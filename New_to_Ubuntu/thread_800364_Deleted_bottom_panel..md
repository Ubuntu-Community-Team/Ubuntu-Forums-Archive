---
title: "Deleted bottom panel."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by KrisScofield on 2008-05-19
While attempting to install AWN navigator, I deleted the bottom panel. How would I get that back? /noob. :confused:

---

### Post by muadnu on 2008-05-19
Right click on the upper panel and then click on new panel... You will have to add then to the new panel whatever you want to put there (windows selector, workspace selector, etc...)

---

### Post by drs305 on 2008-05-19
Right click your remaining panel, select new panel, then drag it where you want it.

Once you have added icons and 'built' your panel, you can save it by running the following in terminal. The saved file will be named panel_settings and will be on your Desktop. Of course you can name it anything and move it wherever you wish:
```
gconftool-2 --dump /apps/panel > ~/Desktop/panel_settings
```

To restore lost panel shortcuts:
```
gconftool-2 --load ~/Desktop/panel_settings
```

---

### Post by KrisScofield on 2008-05-20
Thank you! But I wasn't specific enough, I meant to ask how to create a new panel, and make it so that I can minimize windows and apps into it again? I made a new panel, but can't open minimized windows/apps from it.

---

### Post by HotShotDJ on 2008-05-20
Right click on the bottom panel, click Add to Panel, choose Window List.

---

### Post by Psyker7 on 2008-05-20
Right click the panel -> Add

And look for the one called "Window List"

ugh beaten :P

---

### Post by KrisScofield on 2008-05-20
Thanks! (both of you):)

---

### Post by KrisScofield on 2008-05-20
How would I add nm-applet (the wireless network monitor with the bars) to my new panel? It doesn't seem to be under add to panel.

---

### Post by HotShotDJ on 2008-05-20
> **KrisScofield said:**
> How would I add nm-applet (the wireless network monitor with the bars) to my new panel? It doesn't seem to be under add to panel.nm-applet should appear automagically in your notification area.  Perhaps you removed your notification area when you deleted your bottom panel?  Just add the notification area.  This SHOULD do the trick.

---

### Post by Ripfox on 2008-05-20
Yep add a notification area.

---

