---
title: "Firefox crashes after upgrading to 12.04"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by amit112amit on 2012-04-30
Hi all.
I recently upgraded from Ubuntu 11.10 to Ubuntu 12.04.
But now my Mozilla Firefox crashes as soon as I start it.
I have tried purging and re-installing again from Software Centre and also Synaptic Package Manager, but to no avail.
I am using Gnome 3.4.1 Desktop environment with Ubuntu 12.04(64-bit).

Following error report gets generated to be sent to Mozilla.

[HTML]Add-ons: flashaid@lovinglinux.megabyet.net:2.2.3,ubufox@ubuntu.com:2.0.2,globalmenu@ubuntu.com:3.2.3,{972ce4c6-7e08-4474-a285-3208198ce6fd}:12.0
BuildID: 20120423122928
CrashTime: 1335782151
EMCheckCompatibility: true
Email: amit112amit@yahoo.co.in
FramePoisonBase: 7ffffffff0dea000
FramePoisonSize: 4096
InstallTime: 1335552689
ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 12273
StartupTime: 1335782149
Theme: classic/1.0
Throttleable: 1
Vendor: Mozilla
Version: 12.0

This report also contains technical information about the state of the application when it crashed.[/HTML]

Please help me install Mozilla Firefox.

Regards,
amit112amit

---

### Post by kc1di on 2012-04-30
you can try this go to your home folder , select view hidden files and delete the .mozilla directory.  then re-install Firefox see if that helps.

---

### Post by amit112amit on 2012-04-30
Thanks a lot, Dave.
Its working now.

Regards,
amit112amit

---

### Post by kc1di on 2012-04-30
> **amit112amit said:**
> Thanks a lot, Dave.
Its working now.

Regards,
amit112amit

your welcome please take the time to mark thread as solved :)

---

### Post by amit112amit on 2012-04-30
Yes... I just did that.
This is first time I have asked for help on the forum.
And it was great that I did!

Thanks again.

---

### Post by iamronen on 2012-05-16
but wouldn't that delete all personal preferences/settings?
(I'm having the same problem)

---

### Post by amit112amit on 2012-05-19
Yes it will delete preferences and settings.
But I did not have much except a few add-ons.

- amit112amit

---

### Post by iamronen on 2012-05-20
is there way a to do this without causing collateral damage?

---

### Post by amit112amit on 2012-05-20
I am sorry. I am not an ubuntu expert.
I have already marked this thread as solved.
May be you can start a new thread. Surely some experts will come to your rescue.
- amit112amit

---

### Post by zombifier25 on 2012-05-20
> **kc1di said:**
> you can try this go to your home folder , select view hidden files and delete the .mozilla directory.  then re-install Firefox see if that helps.

Is that a little draconian? You can simply start Firefox in safe mode.

---

