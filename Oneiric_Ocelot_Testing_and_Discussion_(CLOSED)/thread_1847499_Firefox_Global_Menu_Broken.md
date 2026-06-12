---
title: "Firefox Global Menu Broken?"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by teejay17 on 2011-09-20
I'm up-to-date as of this evening, and I'm just wondering if something is broken, or if there's been a reversion somewhere?
My Firefox Global menu seems a little "off." I have the menus in the Unity panel like normal, but I also have two orange X buttons, 2 minimize and 2 maximize buttons -- one set in the panel, and one set just above the first tab. Essentially, it looks like Ubuntu did in the "old" days when maximizing Firefox put it underneath the top panel.

---

### Post by teejay17 on 2011-09-21
> **teejay17 said:**
> I'm up-to-date as of this evening, and I'm just wondering if something is broken, or if there's been a reversion somewhere?
My Firefox Global menu seems a little "off." I have the menus in the Unity panel like normal, but I also have two orange X buttons, 2 minimize and 2 maximize buttons -- one set in the panel, and one set just above the first tab. Essentially, it looks like Ubuntu did in the "old" days when maximizing Firefox put it underneath the top panel.

I looked into this a little further. I have two test machines, one if fine and on the one that is causing the issue above I did two things different:
[LIST]
[*]installed Chrome by command line (which included sudo apt-get install libnspr4-0d and sudo apt-get install libcurl3 dependencies)
[*]also installed sudo apt-get lubuntu-desktop as another UI.
[/LIST]
I'm thinking that either of these two changes may have caused duplicate minimize buttons, etc.

---

