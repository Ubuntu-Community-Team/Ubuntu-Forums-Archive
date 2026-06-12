---
title: "Rinstall and retain settings"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by David1000 on 2008-05-02
My Ubuntu 8.04 is all screwed up after an upgrade from 7.10.  I therefore wish to do a clean reinstall but retain settings and preferences from all my programmes.

My data is on /home so no problem.  I have a copy of /etc/fstab for mount points.  Are there any other directories I should retain - copy back?  I read that one should retain /user/local (better still, put it on its own partition) but this advice may be out-of-date now.

---

### Post by nowshining on 2008-05-03
sll of your settings, prefs, etc.. for you are retained in your /home/username/ folder, just copying it somewhere safe externally off the main OS hard drive and once done re-installing should do the trick, however some things may need to be re-set + that all applicaitons will need to be re-installed.

---

### Post by Paqman on 2008-05-03
With a copy of /home you should be good to go.

Make sure you set your users up in the same order (or at least with the same user id's) as before, or you'll get permissions problems when trying to use your backed-up /home.

---

