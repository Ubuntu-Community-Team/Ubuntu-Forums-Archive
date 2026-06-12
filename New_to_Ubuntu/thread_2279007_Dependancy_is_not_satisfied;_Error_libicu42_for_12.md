---
title: "Dependancy is not satisfied; Error libicu42 for 12.04"
date: 2015-05-20
forum: New to Ubuntu
---

### Post by karthik24 on 2015-05-20
Hi,



When I'm trying to install a software in my Ubuntu 12.04, it shows Dependancy is not satisfied; Error libicu42. But I'm on 12.04. Libicu42 for 10.04, I dont know the logic of the issue here. I tried to install Libicu42 through Terminal, it showed Unable to locate package. I downloaded the libicu42 from the Ubuntu Repository and successfully installed. Then I tried the same software installation; Getting the same issue "Dependancy is not satisfied; Error libicu42". When I checked in Software Center, there is no libicu42 under installed. I tried to install Libicu48 (which is the same package for 12.04) through Terminal, it showed Unable to locate package. Done with the Ubuntu Updates and still the same issue when tried to install Software. Synaptic manager is not installed and tried to install Synaptic manager but Please advise me the work around here. Thanks for reading.

Note:
For this issue there is a previous thread is closed (not created by me :))and it shows moved to general help. But I did not get any solution for this issue on General.

---

### Post by dino99 on 2015-05-20
please post the output of>  cat /etc/apt/sources.list

---

### Post by Vladlenin5000 on 2015-05-20
> **dino99 said:**
> please post the output of

^^^^
This and what software are trying to install exactly? Older software may not work in newer OS versions, as usual, and that dependency suggests this is your case.

---

### Post by newb85 on 2015-05-20
We really need to know what you're trying to install.  It looks like libicu** is in the Main Repository, and is required for a lot of packages that are part of the default installation.  So it sounds like you're trying to install an older package (not from the repos) that won't jibe with the version of libicu in 12.04.

---

### Post by karthik24 on 2015-05-21
You are right. That is my question. libicu42 is not compatible for 12.04. But any software trying to install shows "Dependancy is not satisfied; Error libicu42". I tried to install libicu48 (comaptible with 12.04), its too done successfully. When I tried to install any software after this again the same issue, "Dependancy is not satisfied; Error libicu42". When I checked in Software Center there is no libicu42 and 48. Even I installed the 48 and 42 from [FONT=Arial][SIZE=2][http://launchpadlibrarian.net/199763040/libicu48_4.8.1.1-3ubuntu0.5_i386.deb](http://launchpadlibrarian.net/199763040/libicu48_4.8.1.1-3ubuntu0.5_i386.deb)  [/SIZE][/FONT][FONT=Arial][SIZE=2][http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu48_4.8.1.1-3ubuntu0.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu48_4.8.1.1-3ubuntu0.5_amd64.deb). , still the same issue.[/SIZE][/FONT]

---

### Post by dino99 on 2015-05-21
a #2 post answer is still awaited

---

### Post by VMC on 2015-05-21
> **karthik24 said:**
> You are right. That is my question. libicu42 is not compatible for 12.04. But any software trying to install shows "Dependancy is not satisfied; Error libicu42". I tried to install libicu48 (comaptible with 12.04), its too done successfully. When I tried to install any software after this again the same issue, "Dependancy is not satisfied; Error libicu42". When I checked in Software Center there is no libicu42 and 48. Even I installed the 48 and 42 from [FONT=Arial][SIZE=2][http://launchpadlibrarian.net/199763040/libicu48_4.8.1.1-3ubuntu0.5_i386.deb](http://launchpadlibrarian.net/199763040/libicu48_4.8.1.1-3ubuntu0.5_i386.deb)  [/SIZE][/FONT][FONT=Arial][SIZE=2][http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu48_4.8.1.1-3ubuntu0.5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu48_4.8.1.1-3ubuntu0.5_amd64.deb). , still the same issue.[/SIZE][/FONT]

What program are you trying to install?

Also what's the output of:
```
dpkg -l libicu*
```

---

### Post by karthik24 on 2015-05-21
I tried Skype and McAfee for Linux.  I did not open my laptop yet as I had busy schedule.  I will post the output of **dpkg -l libicu* **and **cat /etc/apt/sources.list **soon. Thank you.

---

### Post by Vladlenin5000 on 2015-05-21
"McAfee VirusScan Enterprise for Linux" is compatible with Ubuntu 10.04, 11.04, 11.10, 12.04, 13.10 only. The dependency probably comes from here, even if it says it's also for 12.04. I would try to uninstall McAfee before anything else.
Skype installed normally shouldn't be the cause.

---

### Post by monkeybrain20122 on 2015-05-21
"McAfee VirusScan Enterprise for Linux" sounds like a scam that costs $. You don't need antivirus on Linux.

---

### Post by Vladlenin5000 on 2015-05-21
> **monkeybrain20122 said:**
> "McAfee VirusScan Enterprise for Linux" sounds like a scam that costs $.
It is and it costs a lot in yearly licenses.

> You don't need antivirus on Linux.
+1

---

### Post by newb85 on 2015-05-22
+1.

Not to mention it needlessly uses system resources.

---

