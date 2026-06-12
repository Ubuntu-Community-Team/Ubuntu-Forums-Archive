---
title: "Limiting processor usage for a particular application"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by Anuovis on 2012-05-12
I have this Windows app that I run through Wine and it tends to consume both of my Intel Centrino Duo cores up to 100% usage. At that point the computer becomes laggy and unresponsive. There is no reason to eat up so much resources so I would like to limit the usage somehow.

Would it be possible to add a resource cap on Wine? Maybe limiting it to one core might be helpful as well.

I tried searching for tutorials but they seem to be very complicated and somewhat outdated. Is there a simple and safe way to accomplish this?

Any tips would be much appreciated.

---

### Post by brainwash on 2012-05-12
You could use the **renice** command to alter the priority of any running process and/or the **taskset** command to change the CPU affinity:
```
man renice
man taskset
```


There is also a tool called **cpulimit** which has to be compiled from source.
Unfortunately I am not familiar with this program. It might be even outdated.

[http://cpulimit.sourceforge.net/](http://cpulimit.sourceforge.net/)

---

### Post by jmszr on 2012-05-12
Anuovis,

Cpulimit is available in the repositories; you can get it from the Ubuntu Software Center. Here is a link to the Ubuntu Geek tutorial on it: [http://www.ubuntugeek.com/cpulimit-limit-the-cpu-usage-of-a-process.html#more-4165](http://www.ubuntugeek.com/cpulimit-limit-the-cpu-usage-of-a-process.html#more-4165) , also: [http://ubuntuguide.net/howto-view-and-limit-process-cpu-usage-in-ubuntu-linux](http://ubuntuguide.net/howto-view-and-limit-process-cpu-usage-in-ubuntu-linux) .

Hope that helps.

---

### Post by Anuovis on 2012-05-12
Thank you, CPULimit did the job.

---

