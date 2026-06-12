---
title: "Old Problem, New Release?"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-08-20
Once again, the age-old update-apt-xapi taking 100% of CPU for an extended period of time has cropped-up in my Oneiric install. I thought this was supposed to be fixed back in Natty?

Any ideas where to start a debug and stop the madness?

---

### Post by lucazade on 2011-08-20
I've seen the same here just a few times in Oneiric.
I believe you can stop it, just as work around, by removing the entry in crontab
"/etc/cron.weekly/apt-xapian-index"
If you open a bug (ubuntu-bug apt-xapian-index) I'll confirm it

---

### Post by MacUntu on 2011-08-20
Is it causing any issues?

---

### Post by lucazade on 2011-08-20
> **MacUntu said:**
> Is it causing any issues?

nothing particular, just made my netbook unusable for 10 mins because of full cpu usage.

---

### Post by MacUntu on 2011-08-20
Ok, then it's a bug as (AFIAK) it's supposed to run at a very low priority.

---

### Post by moore.bryan on 2011-08-20
> **lucazade said:**
> I've seen the same here just a few times in Oneiric.
I believe you can stop it, just as work around, by removing the entry in crontab
"/etc/cron.weekly/apt-xapian-index"
If you open a bug (ubuntu-bug apt-xapian-index) I'll confirm it
Yeah, I know how to stop it... just thought this "problem" was fixed already. :-)

Thanks and I opened a bug:
[https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/830333](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/830333)

---

