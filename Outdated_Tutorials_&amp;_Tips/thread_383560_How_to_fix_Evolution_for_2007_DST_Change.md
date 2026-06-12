---
title: "How to fix Evolution for 2007 DST Change"
date: 2007-03-13
forum: Outdated Tutorials &amp; Tips
---

### Post by woodgdo1 on 2007-03-13
Ok, this is a bit late, but as there was no fix released, I made my own. Basically you need to edit the timezone file for your timezone/City in the file: /usr/share/evolution-evolution-data-server-x.x/zoneinfo/America/YourCity.ics

Here is the unified diff for Chicago CST-CDT 

```
--- Chicago.ics.orig    2007-03-13 09:58:29.000000000 -0500
+++ Chicago.ics 2007-03-13 09:51:31.000000000 -0500
@@ -9,14 +9,14 @@
 TZOFFSETTO:-0600
 TZNAME:CST
 DTSTART:19701025T020000
-RRULE:FREQ=YEARLY;BYMONTH=10;BYDAY=-1SU
+RRULE:FREQ=YEARLY;BYMONTH=11;BYDAY=1SU
 END:STANDARD
 BEGIN:DAYLIGHT
 TZOFFSETFROM:-0600
 TZOFFSETTO:-0500
 TZNAME:CDT
 DTSTART:19700405T020000
-RRULE:FREQ=YEARLY;BYMONTH=4;BYDAY=1SU
+RRULE:FREQ=YEARLY;BYMONTH=3;BYDAY=2SU
 END:DAYLIGHT
 END:VTIMEZONE
 END:VCALENDAR

```

---

### Post by atomizer on 2008-10-20
could not find such a file so made an own workaround (very simple)

I set the evolution time + 1 hour extra (for me I set gtm +2 hours instead of gtm + 1hour, that I need)

Works.

---

