---
title: "Firefox &amp; T-bird can't relate"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by baracuda68 on 2008-05-09
Hi.
Since installing Hardy, My links in Thunderbird don't trigger Firefox 3b5,
and links in Firefox 3b5 don't trigger my Thunderbird.

How do I make them recognize each other?
I do already have them each set as the " default apps" in system settings:
(thunderbird %u)  and (firefox-3.0 %u)

Thanks.:confused:

---

### Post by baracuda68 on 2008-05-11
*Bump*
What? No ideas?
Am I in the wrong forum?:confused:

---

### Post by nowshining on 2008-05-11
alt+f2 kcontrol

KDE components - Default applications - Web Browser - mark in the following browser and input swiftfox or whatever u use and try again.

---

### Post by baracuda68 on 2008-05-11
> **nowshining said:**
> alt+f2 kcontrol

KDE components - Default applications - Web Browser - mark in the following browser and input swiftfox or whatever u use and try again.
Yeah, thanks nowshining,
but as stated above,I have both already as "default". :-?

---

### Post by nowshining on 2008-05-12
oh and sorry not swiftfox - firefox.. :) 

and oh! i didn't see that..or I wasn't paying enough attention...

then u'll have to go into prefs in thunderbird and about:config in firefox and do it manually. about:config u put in the address bar of firefox.

---

### Post by stevebakerj on 2008-05-12
In Fx open about:config and check the following line:

"network.protocol-handler.app.mailto"   is set to  "/usr/bin/thunderbird"  or wherever you have Tb executable located.

and In Tb open about:config and check the following line:

"network.protocol-handler.app.http"   is set to    "/usr/bin/firefox"  or wherever you have Fx executable located

Minus the " "s

---

