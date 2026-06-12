---
title: "[SOLVED] Is there a way to apply all updates automatically?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-07-09
I am setting up Hardy Heron for my parents who are not very tech oriented.  Is there any way to have Ubuntu automatically install all the updates it receives instead of clicking on the alert and putting in a password?

---

### Post by Elfy on 2008-07-09
I think you can get security updates to install without confirmation - update tab of software sources.

Never tried it so don't know if does so without password, but you could also turn off the other updates so it only ever does security updates.

---

### Post by fmartinez on 2008-07-09
use a cron job
#man crontab

---

### Post by curiousnoob on 2008-07-09
> **fmartinez said:**
> use a cron job
#man crontab
What is the advantage of doing it this way compared to the first suggestion?

---

### Post by Elfy on 2008-07-09
I also had another thought - but forgot till the thread came up again - if your parents are not too tech it might be an idea to only have the security updates enabled once you know everything works ok for them - there is less likelihood of things breaking with security updates than other things I'd guess.

---

### Post by Canis familiaris on 2008-07-09
> **forestpixie said:**
> I also had another thought - but forgot till the thread came up again - if your parents are not too tech it might be an idea to only have the security updates enabled once you know everything works ok for them - there is less likelihood of things breaking with security updates than other things I'd guess.

+1
Though rare, Updates may cause problems.

---

### Post by Elfy on 2008-07-09
openoffice being a case in point - although not sure as I got it from proposed :D

---

### Post by LowSky on 2008-07-09
you could always create your own script to do the install automaitcally when they log on

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

[http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/)

---

### Post by curiousnoob on 2008-07-09
> **forestpixie said:**
> I also had another thought - but forgot till the thread came up again - if your parents are not too tech it might be an idea to only have the security updates enabled once you know everything works ok for them - there is less likelihood of things breaking with security updates than other things I'd guess.

That is an excellent point I had not thought of.  Thanks, I think that I will do it that way.

---

### Post by Elfy on 2008-07-09
> **curiousnoob said:**
> That is an excellent point I had not thought of.  Thanks, I think that I will do it that way.

It's how I do it for people I have got using it - when I know I don't want to be fielding daily phone calls :)

Glad I could help.

---

