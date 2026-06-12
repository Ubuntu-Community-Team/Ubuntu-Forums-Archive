---
title: "Google Calendar Remind Script"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-01-15
Hi Folks,

I want to have my Google calendar events displayed in a popup window every so often.

I have a script that works in the terminal.
```
#!/bin/bash
wget https://www.google.com/calendar/ical/url to my calendar/basic.ics
cat /home/grouchygaijin/basic.ics | ical2rem.pl > ~/.ical2rem
rm /home/grouchygijin/*.ics
/home/grouchygaijin/scripts/rg
```

(rg is just another script I have that calls a popup window for my remind file.)

The problem is that if I try to run this script as a cron job (gnome schedule) it chokes when it gets to the part to pipe the basic.ics to ical2rem.pl

Any idea why this will work if I type the name of the script in the terminal but not work if I try to schedule the script to run automatically?

I figured it out.  I needed to give the full path the the ical2rem.pl script.

---

