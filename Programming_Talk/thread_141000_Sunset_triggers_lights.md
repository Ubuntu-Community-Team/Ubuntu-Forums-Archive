---
title: "Sunset triggers lights"
date: 2006-03-07
forum: Programming Talk
---

### Post by pbaehr on 2006-03-07
Many of my lights are controlled via X10 by my Ubuntu machine. I use a program called bottlerocket to communicate with the X10 controller.

Currently, I use cron to trigger several scripts throughout the day. For example, at 6AM various lights begin to fade on for 45 minutes to assist me in getting my *** out of bed.

What I'd like to try to set up is a program that either calculates (seems hard) or looks up the time for sunset each day and triggers a shell script to begin fading in lights to compensate for the failing natural light.

Any thoughts on how it should be set up? It is proving a more complicated undertaking than I'd originally thought.

---

### Post by thumper on 2006-03-07
It looks like weather.com has sunrise and sunset times.

Perhas some from of HTTP query and some HTML results processing to get the times.

I do think though that instead of cron, you'd need some deamon process running.  Perhaps on HTTP failures it could use the time that it worked out for yesterday.

---

### Post by lovebyte on 2006-03-07
All sunrise/sunset data are available:
[http://aa.usno.navy.mil/data/docs/RS_OneYear.html](http://aa.usno.navy.mil/data/docs/RS_OneYear.html)

Enjoy!

---

### Post by pbaehr on 2006-03-07
Yeah, I was already thinking that a daemon would be the way to go. It doesn't seem feasible to have something change the cron entry every day.

I came across the site you reference above and figured it would probably be pretty difficult to get the computer to understand the data the way it's set up.

I also found out that there is a php function that returns the sunset (or sunrise) time pretty easilly. I was thinking about setting up a page locally that calculates the sunset time so that the program could grab it from there...

Thanks for the input.

---

