---
title: "data back up"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Dawid2 on 2008-09-17
Hi Everyone,

I'd like to learn how to back up my hard drive within Ubuntu (8.04 I believe.) In the past when I used (note: past tense) Windows I used Norton's Ghost. I have two hard drives set up master/slave. Is there a utility within Ubuntu or is there one I can download? Remember I'm a new at this so be gentle. All the best, Dawid

---

### Post by billgoldberg on 2008-09-17
> **Dawid2 said:**
> Hi Everyone,

I'd like to learn how to back up my hard drive within Ubuntu (8.04 I believe.) In the past when I used (note: past tense) Windows I used Norton's Ghost. I have two hard drives set up master/slave. Is there a utility within Ubuntu or is there one I can download? Remember I'm a new at this so be gentle. All the best, Dawid

Try the clonezilla live cd.

This is what it says on their webpage:

> You're probably familiar with the popular proprietary commercial package Norton Ghost®, and its OpenSource counterpart, Partition Image. The problem with these software packages is that it takes a lot of time to massively clone systems to many computers. You've probably also heard of Symantec's solution to this problem, Symantec Ghost Corporate Edition® with multicasting. Well, now there is an OpenSource clone system (OCS) solution called Clonezilla with unicasting and multicasting!

Website: [http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by aeiah on 2008-09-17
if you want a solution that incrementally backs up data depending on changes etc then the linux standard is amanda. there's a backup tool called sbackup that comes with ubuntu that is a bit simpler which you may want to look at. bacula is also good apparently. you may be happy with just backing up whole partition sets etc depending on your reasons for backing up

---

