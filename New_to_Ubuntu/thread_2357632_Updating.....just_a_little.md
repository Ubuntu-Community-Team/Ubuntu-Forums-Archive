---
title: "Updating.....just a little?"
date: 2017-04-04
forum: New to Ubuntu
---

### Post by Greg Mueller on 2017-04-04
I just noticed I am still running Kubuntu 12.04.
Is there a way to upgrade just to 14.04 ?

---

### Post by Autodave on 2017-04-04
Yep: and even to 16.04 which is the newest long term release. However, you will have a lot of updating to do. And in my experience, release upgrades don't normally work well. My recommendation would be to back up everything and do a clean install. You will have to re-install all of your programs that you previously installed. However, it will probably take less time to do that than to go through 2 upgrades.

---

### Post by Greg Mueller on 2017-04-04
I only want to upgrade to 14.04
Is there a way to do it?

---

### Post by deadflowr on 2017-04-04
You can from the command line with
```
do-release-upgrade
```
this will upgrade to the 14.04 release.

I forget where the upgrader is graphically, though.
(Though I think it's done through the software updater Kubuntu uses.)

You might need to check that you set the upgrader to LTS releases.
Again, I forget where this is set in Kubuntu, but all version should show in the file at /etc/update-manager/release-upgrades:
look at the Prompt line, options are never, normal, lts, make sure it reads lts.
If not set as lts, change it and then re-run a system update >> sudo apt-get update < then run the do-release command above.

---

### Post by RobGoss on 2017-04-05
Performing a fresh installation is the best way to go, avoid all the problems that come from skipping distributions and trying to upgrade within the system you will be glad you did. Take note, make a complete backup of any important data you want to save

---

### Post by Greg Mueller on 2017-04-05
I have too much information on my computer that I don't want to lose.

---

### Post by tdawgf on 2017-04-05
I would suggest a backup and reinstall. I used the upgrade utility to go from 14.04 to 16.04, and it destroyed my X configuration, and possibly a few other things (I wasn't paying absolute attention to what I was doing). I know it isn't an option for everyone, but I recommend keeping something like a 500Gb or 1Tb external drive for these situations.

---

### Post by Impavidus on 2017-04-05
In my experience, upgrades work. But that's not guaranteed. The cleaner your system is, the more likely the upgrade will succeed, and I always keep my computers clean. So you can simply try the release upgrade to the next LTS release and it should give you 14.04. But be prepared to do a clean install anyway in case it fails.

You have too much information you don't want to loose? Then I assume you already have backups. No? Then make it a habit to create them. If you do a clean install, use those backups to get your files back.

---

### Post by Greg Mueller on 2017-04-05
Thank god I did a Clonezilla complete disk backup before I started.
I'll never do another upgrade ever again

---

