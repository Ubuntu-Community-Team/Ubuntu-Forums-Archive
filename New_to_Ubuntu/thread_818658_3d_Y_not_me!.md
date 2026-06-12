---
title: "3d Y not me!"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Fullblown on 2008-06-04
We'll it's quite obvious that 8.4 isn't really ready for release, it's been 2 weeks and all I've tried to do is switch my special effects to the 3d cube destop and now I'm more confused now then when I started.  This is after a week course to refresh my unix from University.
If someone has step by step instructions I'd be happy to look them over and give it a shot, but there seems to be alot of red tape here and there, and I have ALOT of time at work.  .If someone does and doesn't mind posting it please don't leave any minor detail out. thx.
I'd like to accomplish atleast 1 task before the monitor goes flying accross my lab.

---

### Post by kellemes on 2008-06-04
Please post specs.

---

### Post by sayakb on 2008-06-04
Check the Desktop Cube and Rotate Cube options in ccsm. If you don't have ccsm,
```
sudo apt-get install compizconfig-settings-manager
```

Make sure you have compiz running (You have desktop effects?)
Also, in ccsm goto General options-> Desktop and set Horiz. virtual size >=4
(PS: 5 will give a 3d pentagon!!)

---

### Post by JoshuaRL on 2008-06-04
Yeah, we need your computer type and specs, what you installed, what errors you have, what graphics card, and what you've tried.  We can go from there.

---

### Post by dracayr on 2008-06-04
```
sudo apt-get install simple-ccsm
```
then, go to the appearence settings, and check userdefined in the effects tab. Go to System->preferences->Simple compiz config settings manager (At least that's what I think it is, I'm translating from german),click on workspaces, and choose Desktop cube.

dracayr

---

### Post by Fullblown on 2008-06-05
Ok thanks for the responses it appears I was somewhat correct as my display driver is on the blacklist "intel".  Guess I'll just have to wait until 8.10 to come out.

---

### Post by SunnyRabbiera on 2008-06-05
are desktop effects that important to you?
well instead of heading back to vista land I suggest giving mandriva a try if you are that wanting for desktop effects.
The intel driver you have was probably blacklisted for a reason though, I know there were many that were causing too many issues to count.
But if needed you can ask around on how to unblacklist it.

---

