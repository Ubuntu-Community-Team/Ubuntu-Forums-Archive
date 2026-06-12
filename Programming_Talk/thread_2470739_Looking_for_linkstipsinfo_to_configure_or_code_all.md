---
title: "Looking for links/tips/info to configure or code all boxes to use GPS"
date: 2022-01-09
forum: Programming Talk
---

### Post by ccor58 on 2022-01-09
I have Xplornet as an ISP and the location software on all commercial or public websites extracts my location from what the ISP provides for the browsers to use. In my case it is wrong and can be anywhere from Alberta to Ontario & New Brunswick depending on what point of presence Xplornet is set to connect me through. It is a capital pain and I would like to see if I can get some coding or adjust some other setting in browsers to read a simple $25 GPS USB receiver for my actual location instead of relying on what ISP's apparently consider to costly to correct.

Any code snippets or PC apps linux preferred but if built into a browser it would be a big help cross platforms.

Thanks from the Oldies Heartland

---

### Post by TheFu on 2022-01-09
Each webpages probably uses a different "Geolocation" lookup DB that only looks at the current IP address. Most people block GPS access - I do on all platforms - sometimes google and I get into fights about getting access to correct GPS in Android, but my computers basically never provide GPS, since they don't have any GPS data and providing it to a browser would be extremely bad for security.

I take it you've never been stalked?  I have.

---

