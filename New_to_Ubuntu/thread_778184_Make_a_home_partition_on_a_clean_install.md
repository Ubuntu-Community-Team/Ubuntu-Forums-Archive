---
title: "Make a home partition on a clean install"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-01
Needless to say my upgrade failed. So now if I do a clean install how do I create a separate partition for the home folder in case something like this happens again? When Hardy boots up it gives me an error message about HAL

---

### Post by aheckler on 2008-05-01
Boot to the LiveCD and when you get to the partitioning part, choose manual, and the create a root partition at the beginning of your drive with maybe 10-15 GB worth of space, a swap partition on the end of the drive of about 1 GB space, and a /home partition as the rest.

EDIT: This guide will help. Scroll down a bit til you get to the partitioning section: [http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

---

