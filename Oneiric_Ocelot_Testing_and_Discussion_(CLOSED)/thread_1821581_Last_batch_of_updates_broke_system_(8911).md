---
title: "Last batch of updates broke system (8/9/11)"
date: 2011-08-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Curnel_D on 2011-08-09
Just updated about half an hour ago.  After reboot, I get a blank screen.

No idea which update caused it, nor do I have any idea how to find out.

Is there any way I can do a rollback?

---

### Post by 3vi1 on 2011-08-09
I see this too - on my CR-48.

I can still boot in safe mode and get Unity2d running, but I can't get the 3D desktop to start at all.  :\

---

### Post by 3vi1 on 2011-08-09
Looks like new Intel drivers just hit the repos - fixing the problem.

Boot in safe mode, choose the netroot prompt, then 'apt-get update && apt-get upgrade && reboot', and you should be good to go.

---

### Post by Curnel_D on 2011-08-09
Fixed.  I could do the same.

I just booted into recovery mode and repaired packages.

For me, it was the latest intel-Xorg driver update.

Edit: Heh, beat me to it.

---

