---
title: "Keyboard not responding in Dash search bar"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by souravc83 on 2012-03-09
I have a weird problem.
When I go to the Unity dash search bar, I cannot type anything into it. After 7 or 8 keypresses, It will probably register one random keypress, and then again ignore the rest.

My keyboard also sometimes (rarely though) goes randomly unresponsive in gedit or chrome address bar. If I open another gedit document and type in, then again everything becomes normal.

I have no idea what is causing the problem. I am running Ubuntu 11.10 in a Lenovo Thinkpad T61. Its definitely not a crappy keyboard issue, since it happens systematically at the Dash search bar every time.

---

### Post by Script Warlock on 2012-03-09
> **souravc83 said:**
> I have a weird problem.
When I go to the Unity dash search bar, I cannot type anything into it. After 7 or 8 keypresses, It will probably register one random keypress, and then again ignore the rest.

My keyboard also sometimes (rarely though) goes randomly unresponsive in gedit or chrome address bar. If I open another gedit document and type in, then again everything becomes normal.

I have no idea what is causing the problem. I am running Ubuntu 11.10 in a Lenovo Thinkpad T61. Its definitely not a crappy keyboard issue, since it happens systematically at the Dash search bar every time. check the system settings > universal access > typing > bounce keys(should be turned off)

---

### Post by souravc83 on 2012-03-09
Thanks for your reply.
Checked the setting. Its turned off.

---

### Post by Script Warlock on 2012-03-09
any extra usb keyboard to try before reporting this as bug.

---

### Post by monkey21stc on 2012-03-15
Hi I have a similar issue.

I'm currently using the 'super' key to invoke the dash. Usually this scenario is observed:

'super' key, search box not responsive to key press, only a few keys like 'l' ,'k', 'e' and 'j' are recognized.

closing the dash with 'esc' key or mouse click before invoking a second dash via 'super' key would allow the search box to be inputted normally.

A similar bug has been filed in launchpad I believe (don't have link at the moment) 

Would love to see a solution though, as this bug is affecting my workflow, as dash needs to be invoked twice before I can search for anything.

Thanks and regards
Monk

---

### Post by souravc83 on 2012-03-18
Will try with an usb keyboard sometime.
I haven't found a solution.
I am noticing lately though that it responds after a while.
If you repeat a keypress a number of times, it then registers a key after a few seconds. Then I can type in something, and sometimes this will work.

---

### Post by crobitaille on 2012-03-31
I am getting a similar problem as [monkey21stc]("http://ubuntuforums.org/member.php?u=1084771") but I have a little more info. In my case, occasionally (once a day or twice) will lockup but usually only for a specific application/window. Other applications are Ok. Some time, but rarely, it is a mouse button that is freezing but in that case, the whole GUI is affected. In most cases, 'super' W and back unfreeze the keyboard (which was not totally frozen since the 'super' key worked).

The more info I have is that I am using multiple keyboard layout (US and Canada multilingual). The problmem is not specific to one of the layout but may be simply related to the fact that I have the support for different layout enabled.

---

### Post by jdeakin on 2012-07-17
This happened on our system when someone accidentally pressed on a key and held it down for a long time. The keyboard then stopped working unless you kept pressing it!

Solution:

Applications > System Tools > System Settings > Universal Access > Typing

Set slow keys = OFF (and everything else for that matter!)

Good luck!

---

