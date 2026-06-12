---
title: "Battery icon is missing if the battery is inserted after boot"
date: 2018-07-21
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-07-21
I am running 18.04 LTS

Here are the steps to reproduce this problem.
a) Remove the battery from laptop.
b) Connect laptop to A/C adapter and turn on the laptop.
c) Since there is no battery, we do not see battery icon on ACITIVITY bar.
d) Now connect battery to laptop when the OS is still running.
e) Battery Icon does NOT appear on ACTIVITY bar. I let the OS run for hours, still battery icon did not appear.
f) I turned off the A/C power and machine switched over to battery successfully. This means h/w identified the battery but the GUI did not. 

I turned off the Laptop.
a) Connected battery
b) Turned on the laptop.
c) Battery icon appeared on ACITIVITY bar. 

It seems battery-icon shows up only if the battery is present at the time of booting of OS.

Thanks,

---

### Post by Autodave on 2018-07-21
And that sounds completely normal to me. At boot, it looks to see if it is there. When it doesn't find one, it obviously will not display the icon. Reinserting the battery will not be "noticed".

I am not sure why you would run the laptop without a battery anyhow: not a wise thing to do.  Voltage spikes could damage the laptop: the battery acts like a kind of buffer so that that doesn't occur as easily.

---

### Post by wrongusername2 on 2018-07-27
I agree spike could damage laptop. I have been running on direct A/C for years without any event. I limit battery usage just to prolong the battery life.

---

