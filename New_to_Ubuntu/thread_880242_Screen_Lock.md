---
title: "Screen Lock"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-08-04
When I used to have 7.04 on my laptop, I could close the lid and it would lock the screen. Now I have 8.04, how do I re-enable that. Thanks.

---

### Post by Mister.Vash on 2008-08-06
You may already have this set, but do the following
Go System -> Preferences -> Power Management
and on "ON AC Power"
select Blank Screen for "When laptop lid is closed"
you might want to set the same for "ON Battery Power" as well

Then run gconf-editor
navigate to /apps/gnome-power-manager/lock/ and check blank_screen

---

