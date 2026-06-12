---
title: "Partioning HD for multiple boots"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by jdestruel on 2008-09-30
I have XP and Ubuntu 8.04. I'd like to install Ubuntu 8.10 and a couple of other distros. How do I partition my single HD? I ran out of primary partitions, so I must be doing something wrong.

One primary, one extended and split the extended into more bootable partitions??

Thanks

JC

---

### Post by overdrank on 2008-09-30
Moved to ABT :)
Yes you will have to create a extended partition if you wish to have more that 4 primary partitions.

---

### Post by jdestruel on 2008-09-30
Thanks

---

### Post by Bölvaður on 2008-09-30
you might also want to experiment with sharing /home between distros. it will give you same configuration for distros using it.

---

### Post by gpsmikey on 2008-09-30
I have several ones I have been playing with and share the swap partition between them.  I have seen a discussion somewhere recently on sharing /home directories and a comment was made about running into possible problems with your configuration information (desktop etc) between distro's.  Something to consider (or use a different user name on the different distro's but share the home partition).  As far as number of partitions, you are indeed limited (under normal situations) to 4 primary partitions, however, linux seems to be happy working with extended partitions so there is not a problem that way.

mikey

---

### Post by Therion on 2008-09-30
Just a thought but... This sounds like a job for Virtual Box!

---

