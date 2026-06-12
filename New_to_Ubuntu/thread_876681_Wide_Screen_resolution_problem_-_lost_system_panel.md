---
title: "Wide Screen resolution problem - lost system panel"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by MothHunter on 2008-08-01
I'm trying to set up an LG Flatron W1952TQ wide screen monitor for my father on Hardy Heron 8.04.  The LG website lists the monitors resolution at 1440 x 900 - which Ubuntu lists as being the resolution in use.  However, the 'application-tracker' System Panel, which usually appears along the base of the desktop, is at least an inch below the edge of the screen.  Do I have a resolution issue?  Or is there a setting I have missed somewhere?

Thanks :)

---

### Post by overdrank on 2008-08-01
> **MothHunter said:**
> I'm trying to set up an LG Flatron W1952TQ wide screen monitor for my father on Hardy Heron 8.04.  The LG website lists the monitors resolution at 1440 x 900 - which Ubuntu lists as being the resolution in use.  However, the 'application-tracker' System Panel, which usually appears along the base of the desktop, is at least an inch below the edge of the screen.  Do I have a resolution issue?  Or is there a setting I have missed somewhere?

Thanks :)

Hi and does the monitor have a auto adjust function? My LCD does and I have used it to correct minor issues. If this does not work you may use the command ```
gksu displayconfig-gtk
``` and make adjustments there.
What is the model of the graphics card.

---

