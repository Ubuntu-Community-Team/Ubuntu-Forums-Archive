---
title: "Failed install with alternate CD"
date: 2011-06-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-06-25
I did a zsync to my oneiric alternate ISO, 32 bit, at 15:00 GMT Jun 25.

When I tried to install from the CD it failed.

I downloaded the daily live and it installed as expected.

Has anyone else had problems with the alternate CD?

---

### Post by cariboo on 2011-06-26
Where in the process did it fail. Maybe a bug report needs to be created.

---

### Post by JRV on 2011-06-26
It failed at 18% into the "Select and Install Software" step.

I just tried it on a second machine and it did the same thing.

---

### Post by lonniehenry on 2011-06-26
I tried to do an install yesterday with an alternate disk for 64 bit in Virtualbox and a daily from Friday and they both failed at that step.  Haven't had time to try figure out what went wrong.

---

### Post by JRV on 2011-06-26
> **cariboo907 said:**
> Where in the process did it fail. Maybe a bug report needs to be created.

Since I tried it on a second machine, and lonniehenry has the same problem, a bug report is probably a good idea.

I have filed bug reports using Apport before, but how do I file one where I have to just write it? I've looked all over launchpad and I can't find anything like that.

---

### Post by pressureman on 2011-06-26
You should always check the [report]("http://cdimage.ubuntulinux.org/daily/current/report.html") for the daily alternate ISOs. If there were uninstallable packages for your arch mentioned in the report, chances are pretty good that you'll have errors part way through the install.

---

### Post by tlcstat on 2011-06-27
Greetings,
I have been having problems with the alt CD's from the beginning. They will fail for a few days and then you will have an edition that installs. For me it has always failed in the software installation part. I have a Toshiba and a Dell both with Celeron single core and they both do the same thing. I just keep zsync'ing each day until it works. 
tlcstat

---

### Post by JRV on 2011-06-27
> **pressureman said:**
> You should always check the [report]("http://cdimage.ubuntulinux.org/daily/current/report.html") for the daily alternate ISOs. If there were uninstallable packages for your arch mentioned in the report, chances are pretty good that you'll have errors part way through the install.

I think you got that right.

I had never seen an install fail with the alternate before. That must have been just random luck.

Thread Marked Solved.

---

### Post by tlcstat on 2011-06-28
Greetings,
Well! Today's alternate iso installed just fine. That little ocelot must have connected with my inner oneiric!
tlcstat

---

### Post by AdiRusF on 2011-06-28
Here is failed to install latest build from oneiric
I have adsl connection and ubuntu-alternate wont configure only dhcp and I need username and password so is failed because there is no connection to internet to download the missing dependency for kernel 3.0

---

