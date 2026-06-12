---
title: "[SOLVED] missing wireless signal strength panel app"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by kaston on 2008-06-25
i seem to have somehow lost my wireless signal strength panel app which also allows me to select different wireless networks and connect to my vpns.  it's the one that looks like a blue staircase.  i did a right click on panel>add to panel> network monitor, but that gave me something different.  how do i get my blue staircase back?

---

### Post by Elfy on 2008-06-25
Have you lost your notification area - right click panel and then add it back make sure also that you have it in your sessions - system > preferences

---

### Post by Sub101 on 2008-06-25
If the above doesn't work then try

```
sudo apt-get install nm-applet
```

---

### Post by kaston on 2008-06-25
notification area!  that was it.  thanks.  i don't see any "notification area" in system>preferences though

---

### Post by Het Irv on 2008-06-25
Right click on the panel and click "Add to Panel"  You should see it in that list

---

### Post by Elfy on 2008-06-25
> **kaston said:**
> notification area!  that was it.  thanks.  i don't see any "notification area" in system>preferences though

Sorry - getting ahead of myself again, that actually meant - check in preferences to see if you have the network manager applet in there - but of course as you're not telepathic you didn't get that bit :D

Glad it was just notification panel 

If it's done could you mark thread solved please

---

