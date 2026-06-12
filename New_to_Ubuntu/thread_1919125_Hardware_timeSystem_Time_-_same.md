---
title: "Hardware time/System Time - same?"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by melbs on 2012-02-02
I've done some research and realize they are different and I think hardware time is when the server was created? Then system time is local time..a few questions after this happened yesterday.

We run Moodle on ubuntu linux and yesterday realized the clock was set to Sept. 26th, 2011. I looked and the uptime was about 5 hours on our server so I assumed something went wrong and crashed and rebooted because we hadn't restarted it on purpose.

Then I had my network guy restart the server again hoping it'd take care of it and it didn't. So I went into webmin and saw both the hardware clock and system clock were somehow set to that Sept. day.

I manually changed both clocks to our local time this morning. It seemed to fix the date issue in Moodle but my questions are:


[LIST]
[*]If the server crashes is it common for this date issue to happen?
[*]Should the hardware clock ever be changed? If it is, could it mess things up?
[*]What effect does the hardware clock date and time have on the system date and time?
[*]Is it okay to leave both clocks the same like I have it now?
[/LIST]

THANKS!

---

