---
title: "Problem with wifi radar after 8.10 upgrade"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by track dog on 2008-11-02
After I upgraded to 8.10, the application 'wifi radar' won't launch.  The error message says 'failed to execute child process "su-to-root".  It worked in 8.04.

---

### Post by Partyboi2 on 2008-11-03
Try right click on the Applications panel and select "edit menu" then on search for the wifi radar entry, probably internet (left panel)  >  wifi radar (right panel) and highlight and select "properties" then change
```
su-to-root -X -c /usr/sbin/wifi-radar
```
to
```
gksu /usr/sbin/wifi-radar
```

---

### Post by track dog on 2008-11-07
Thank you! Your suggestion worked!

---

### Post by HeadRoom on 2009-04-18
Worked for me...  found it quick,  Still can't connect to my wireless network tho...  I'll get there eventually.

HR

---

### Post by HeadRoom on 2009-04-18
And now, 5 minutes later, I'm wireless and can see more networks than I can in XP...  finally!  I have been pulling my hair out for weeks over this Atheros card and new Ubuntu install.  Tried mad wifi, and some others, but this worked.  ndis wrapper and wifi radar did the trick.  Much thanks...

---

