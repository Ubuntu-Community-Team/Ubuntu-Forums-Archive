---
title: "Windows partition"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by Ashok1989 on 2012-12-30
Hi Friends,

I'm a beginner to this thread... Sorry if I forgot the equities for posting a thread. 

Actually my query is,

I have xp OS which was installed in the c drive. I want to install ubuntu to d drive. But my d drive has 75GB it couldn't afford to install. So I badly need to increase my d drive. As i searched I got the Gparted to re-size the drive. I reduce the size of E drive and made 15gb free. But that is in the unallocated space of the system. So how can I add those free space in to the d drive. Please suggest a step by step procedure to solve this problem...

Thanks and Regards,
Ashok

---

### Post by gnush on 2012-12-30
75 GB is more than enough for Ubuntu. If you want help increasing the size of that partition, boot Ubuntu using the live cd, open up a terminal and run the following command.

```
sudo fdisk -l
```

When that's done, paste the output in this thread.

---

