---
title: "is LTS version secured after 5 years of support?"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by dixcuxx on 2013-04-10
I am planning to build a lamp server with Ubuntu latest LTS, is it going to be secured after 5 years of support? Thanks.

---

### Post by DuckHook on 2013-04-10
Not sure if I'm answering you properly, but LTS, though extended support, will not last beyond 2017, at which point, it will stop receiving any sort of updates including security. I believe the intent is that we continue moving onwards and upwards, although I believe that there will be at least 6-months overlap between expiring and new LTS.

---

### Post by mastablasta on 2013-04-10
yes if you secure it propperly.

however after 4 years support runs out and you won't get the security updates/patches anymore. so there iwll probably be cores. but you can upgrade after that.

another option would be RHEL (Or centos) which i htink has support until 2019.

---

### Post by dixcuxx on 2013-04-10
so I guess after around 4 years, I have the option to upgrade to the new version of Ubuntu LTS?

---

### Post by DuckHook on 2013-04-10
> **dixcuxx said:**
> so I guess after around 4 years, I have the option to upgrade to the new version of Ubuntu LTS?

Unless Ubuntu has changed their program, it is my understanding that they will release an LTS every other year (even years). So, the next LTS will be 14.04, then 16.04. You will have a full year to convert to 16.04 before 12.04 is dropped in 2017.

You will have fallen so far behind on the "upgrade" cycle though, that you will likely want to install a fresh version instead of just "upgrading". My own preference is to install a clean system with each upgrade anyways, so that I don't inherit obsolete configuration files.

---

### Post by dixcuxx on 2013-04-10
That's cool. So it is very easy for you to setup everything again?

---

### Post by DuckHook on 2013-04-10
> **dixcuxx said:**
> ...very easy for you to setup everything again?

Unfortunately, it isn't. Depends a lot on how well you prepare for it now. It actually turns out to be a little easier on servers because they are mostly about data, don't have a lot of apps, and don't have much personalized stuff spread out all over kingdom come, like e-mail, docs, photos, music, etc that most of us clutter up our lives with. It is inherently easier to migrate, say, one or two databases, than dozens of little persnickety apps for which you have to hunt down each and every data file.

Another advantage to servers is that the all-important data tends to be naturally segregated onto separate HDDs (or at least partitions) from the beginning. This allows the OS to be nuked without affecting the data at all. Last but not least, servers are almost always backed up religiously, so there is no likelihood of data disaster, which is the single biggest problem for casual users. The biggest headache that servers must contend with that the average Joe has the luxury of not caring too much about is uptime requirement.

You probably already see where this is going: if you set up your partitions/HDDs properly beforehand, where data is strictly segregated and you follow an unbending personal discipline when installing your apps, then you can minimize the pain of a future brand new upgrade. oldfred recommends separate data partitions (over and above a separate /home) even for desktop installations. I agree.

I've gotten so used to the backup/install/restore cycle that it doesn't bother me anymore. When I started out with Ubuntu, I tried doing the upgrade thing, but usually ended up spending so much time, effort and frustration hunting down bugs and incompatibilities, and trying to re-tweak the system, that I found it far better for my blood pressure to just do clean virgin installs every time. I keep a journal to track the various exact steps needed for each install and I keep improving it with every new one. Over the years, it's turned into a standardized installation routine that is as painless as such an inherently painful procedure is going to get.

---

