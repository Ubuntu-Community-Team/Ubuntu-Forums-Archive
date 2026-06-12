---
title: "Wireless card stuff"
date: 2007-07-30
forum: Programming Talk
---

### Post by sheol on 2007-07-30
After constant dissapointment with the GUI wireless tools, myself and another have decided to write our own.
We are doing it starting with scripts, and then have plans to integrate a GUI frontend as a seperate package.

Anyway theres something I can't figure out.

When you activate a wireless card.  The system says okay its active.  However it takes several seconds for the card to actually initialize.
In that interim time, if you run 'iwlist scan' it will tell you that there are no networks. (As opposed to device doesn't support scanning like if it is down, or showing networks if it is up and theres something to connect to)

I was wondering if anyone knows of or can think of a way to tell whether a wireless card that has been activated is yet "ready to do stuff"?

Currently we are just having the porgram pause for a few seconds.  However this is very hackish and will either slow down fast systems, or not work on slow systems.

Ideas?

---

