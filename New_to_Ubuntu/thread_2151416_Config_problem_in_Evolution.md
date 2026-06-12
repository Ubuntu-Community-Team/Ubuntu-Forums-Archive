---
title: "Config problem in Evolution"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by Iceberg76 on 2013-06-04
The Evolution Clock Applet is showing the wrong time. It has a discrepancy of 1 hour from my real time.

cat /etc/timezone outputs Europe/Paris, but gconftool-2 -g /apps/evolution/calendar/display/timezone outputs Africa/Algiers. My correct time would be Paris, but the applet is showing the Algiers time.

So, if I have a meeting at 13:00 pm, the applet shows 14:00, adding 1 hours to compensate that Algiers has one hour less than Paris. 

However, through gconf-editor I don't find evolution in apps/evolution.

How can I correct that? 

I am aware that's a minor bug  from old of Evolution. Sometimes it picks the wrong time, but I would be happy with a temporary solution like changing the gconf value (that might last until the next summer time change of the official clock).

---

### Post by Iceberg76 on 2013-06-04
Solved! Strangely, when I edit with sudo gconf-editor I get to see less keys than without gconf-editor. Out of curiosity, I'd like to know the reason for that.

---

