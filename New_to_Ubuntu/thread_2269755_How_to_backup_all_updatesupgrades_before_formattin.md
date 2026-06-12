---
title: "How to backup all updates/upgrades before formatting hard disc"
date: 2015-03-17
forum: New to Ubuntu
---

### Post by newbie13 on 2015-03-17
I have Ubuntu 14.04, Kali Linux and windows installed on my laptop. Lately, windows has been infected with viruses and there are many other issues with it (hard disc is completely full, unknown/unnecessary small partitions etc) so I want to factory reset my laptop. The problem is I have downloaded and installed many updates since april/may 2014 and I can not download everything again after factory reset due to slow and limited internet connection. 

Is there any way to back up both linux partitions completely on external hard disc to restore after reset? Or any other way in which I will not need to download all updates again?

---

### Post by dino99 on 2015-03-18
you can backup with 'deja-dup'
all your updates are into /var/cache/apt/archives/

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by newbie13 on 2015-03-18
Should I add "/" this folder to backup to save all updates?

---

### Post by mastablasta on 2015-03-18
you can use redobackup or clonezilla to create complete image.

also it might be good to install some anti-virus + firewall combo on windows partition.

---

### Post by newbie13 on 2015-03-18
Thanks. I will go through what you have suggested. 
Deja-dup is preinstalled in ubuntu so that will be the easiest way, I guess. Should I add '/' in back up or just 'home' is enough to restore all updates?

I have anti-virus in home since last 3 months but I was too lazy to boot into windows, install everything, activate it and download the updates. Last week my friend's external hard disc infected it with many viruses plus there is a lot of junk in it so I was thinking of completely removing everything so that I will get some room on laptop and windows will become less lagy again.

---

### Post by ian-weisser on 2015-03-18
> **newbie13 said:**
> Should I add '/' in back up or just 'home' is enough to restore all updates?

Neither.
9d9 told you where the updates are (and should be restored to) in post #2 above.
It's the specific location that the package manager expects to find packages at.

---

### Post by newbie13 on 2015-03-18
So I should keep a copy of that folder and place it back after reset, that's it?

---

### Post by ian-weisser on 2015-03-18
For updates, yes.
For your personal data, /home

---

### Post by newbie13 on 2015-03-19
Thank you guys..

---

### Post by deadflowr on 2015-03-19
Two thing about copying the /var/cache/apt/archives folder to consider.
1) if you have ever run the apt-get clean command, then any packages in the archive will be only for packages that have been updated since the clean command was run.
The apt-get clean command clears out that folder. It'll fill up again, whenever any new updates or packages come. But the older updates would be gone.
If that makes sense.
and 
2)You can reduce the size of the archives folder by running the other apt-get command, apt-get autoclean.
The autoclean command only clears out the packages that are no longer installable, or have newer versions, leaving those older packages obsolete.
A common example would be firefox. You might have a package archive for firefox 34 and firefox 35. By using the autoclean command, it'll remove firefox 34, but keep the current firefox 35.
(And yes, I know forefox should be up to firefox 36, but this is only an example)
Hope that helps, at least for later on, maybe.

---

### Post by newbie13 on 2015-03-20
Luckily I haven't run apt-get clean.
If the size of archives gets too big then I will use autoclean.

Thanks

---

