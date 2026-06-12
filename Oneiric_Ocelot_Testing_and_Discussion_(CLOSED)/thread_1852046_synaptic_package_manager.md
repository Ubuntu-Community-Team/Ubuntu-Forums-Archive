---
title: "synaptic package manager"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-09-29
after last updates spm crashes after i enter my password to open. worked great until updates

---

### Post by Harry33 on 2011-09-29
> **rburkartjo said:**
> after last updates spm crashes after i enter my password to open. worked great until updates

Which update that might be?
I do not have such kind of issues in my setups.

---

### Post by rburkartjo on 2011-09-29
harry how can i tell it is was just in the last update.now second to last i always use sudo aptitude update && sudo aptitude safe-upgrade

---

### Post by rburkartjo on 2011-09-29
also ubuntu software center does the same thing

---

### Post by VinDSL on 2011-09-29
> **Harry33 said:**
> Which update that might be?
I do not have such kind of issues in my setups.
I *think* it would be this, Harry:  [http://ubuntuforums.org/showthread.php?t=1852038](http://ubuntuforums.org/showthread.php?t=1852038)

---

### Post by PaulW2U on 2011-09-29
> **VinDSL said:**
> I *think* it would be this, Harry:  [http://ubuntuforums.org/showthread.php?t=1852038](http://ubuntuforums.org/showthread.php?t=1852038)
and here? - [http://ubuntuforums.org/showthread.php?t=1852054](http://ubuntuforums.org/showthread.php?t=1852054)

---

### Post by VinDSL on 2011-09-29
> **PaulW2U said:**
> and here? - [http://ubuntuforums.org/showthread.php?t=1852054](http://ubuntuforums.org/showthread.php?t=1852054)
Yes, that would be it...  :)

I'll post a link to it, in the other thread.

EDIT

Heh!  You beat me to it.

@ cariboo907: I think you need to merge some of these threads.  Just saying...  ;)

---

### Post by PaulW2U on 2011-09-29
The bug has now been marked "Critical" so I'm sure a fix will be along soon.

---

### Post by rburkartjo on 2011-09-29
tks yall at least i wasnt losing my sanity

---

### Post by the_blue_box on 2011-09-29
I am having the same problems AND my update manger doesn't work :(
I can update through the command line though so all is not lost

I hope some fixes come out soon :popcorn:

[COLOR="Navy"]The Blue Box [/COLOR]

---

### Post by Harry33 on 2011-09-29
Hmm, now that is strange.
I do not have issues like that.
Also latest Thunderbird (7.0.1) and Firefox (7.0.1) are working just fine.
I have fully updated setups, all working fine (with the latest libcanberra, 0.28-0ubuntu9).

---

### Post by VinDSL on 2011-09-30
> **PaulW2U said:**
> The bug has now been marked "Critical" so I'm sure a fix will be along soon.
Just returned to my abode, and updated.  Life is good again!

It took a combination of differing mechanisms - apt-get, which begot Synaptic, which begot Aptitude.  Almost like updating winders - update, and update, and update again - and you're good for another 24 hours.

Anyway, I'm ready for you, Canonical.  Bring on the breakage.  LoL!  :D

---

### Post by rburkartjo on 2011-09-30
just updated 5:40 cst software center working but still not synaptic. sure it will be fixed eventually

---

### Post by dino99 on 2011-09-30
sudo synaptic only works here

---

### Post by rburkartjo on 2011-09-30
tks dino will keeping updating. as long as gets fixed eventually in one of the updates

---

### Post by VinDSL on 2011-09-30
Did you guys use apt-get update first?

apt-get listed a huge amount of updates, and one hold (for me).  I don't normally do partial updates, but I made an exception this time.

Then, I did another apt-get update... and another.  Every time, more updates were performed, but the hold remained.  Eventually, nothing was coming up except the one held update.  At that point, I tried Synaptic, and it loaded. Yeah!

Synaptic came up with several more updates, plus it allowed me to install the update being held back by apt-get.  A second refresh was clean (no updates).

Then, I ran apt-get update.  It was clean.  And, Aptitude.  It was clean too.

After doing all of this, I did a cold boot, and everything was back to normal... better than normal, actually.

Heh!  I think I'm going to lay off the updates for a couple of days.  Unity is running too smoothly right now!  ;)

---

