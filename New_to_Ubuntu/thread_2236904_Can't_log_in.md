---
title: "Can't log in"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by oval61251 on 2014-07-29
So I recently bought an HP chromebox and installed Ubuntu via crouton from this [tutorial ]("https://www.youtube.com/watch?v=_xsqrQw1kbs").  I create my username and password without a problem, but if I log out of Ubuntu or power off the chromebox and turn it back on I get brought back to ChromeOS, which is fine.  However when I bring up the terminal by pressing CTRL/ALT/T I get prompted with "Crosh".  From there I dont really know what to do but if I type in "Shell" I Chronos@localhost I have been doing the following to log in sudo enter-chrootsudo startxfce4 which allows me to login as root, which isn't ideal since I want to use chromium browser.  I have been reading and searching for days, but I cant find how I log back into Ubuntu after rebooting or logging out.

---

### Post by oval61251 on 2014-07-30
Anyone? I have been stuck for 3 days now.

---

### Post by Bashing-om on 2014-07-30
oval61251; Patience ...

How many of us run the HP chromebox that can directly reciprocate with your situation ?

A response to a thread that does not contribute to a resolution is NOT encouraged on this forum ( Will I get a slap on the wrist for mine ?)

A bump in 24 hrs ( as the world turns ) is acceptable to regain focus.

I (we) am not familiar with that box's boot process, and thus cannot advise.

[INDENT][INDENT]can't know everything
[/INDENT][/INDENT]

---

### Post by veddox on 2014-07-31
@oval61251:
  I have absolutely no experience with your setup either, but I watched the tutorial you mentioned. Just two suggestions, that may or may not work:

1. Switch user from within the xfce desktop - if that's possible. (Don't log out and back in again, "switch user")

2. Once you're in xfce, press CTRL+ALT+T to bring up an Ubuntu terminal. Then enter the following commands:
```
su <yourusername>
chromium
```
If I'm not mistaken, that should have you running Chromium without root privileges.

Please note that the authors of crouton themselves warn of possible security problems when using their software on their [Github page]("https://github.com/dnschneid/crouton")! So this issue may turn out to be unresolvable. 

I am sorry that you have had to wait a while for an answer, but you do have a rather unconventional setup ;-)

P.S. In future, when posting code segments or terminal commands, please use code tags for better readability.

---

