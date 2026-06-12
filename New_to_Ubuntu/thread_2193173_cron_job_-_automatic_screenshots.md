---
title: "cron job - automatic screenshots"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-12-11
I would like to program the computer to take an automatic screenshot every 10 minutes, as if I had pressed 'prt sc".

I think that means a 'cron job'. If anyone can help me, that would be great.

---

### Post by wlraider70 on 2013-12-11
You might try 

sudo contab -e

10 * * * * gnome-screenshot -w


That could use a little refinement like only businesses hours or saving to a certain directory, but it should work.

---

