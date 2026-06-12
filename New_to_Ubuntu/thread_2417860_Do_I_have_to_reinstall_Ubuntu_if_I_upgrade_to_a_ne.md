---
title: "Do I have to reinstall Ubuntu if I upgrade to a newer version of it?"
date: 2019-04-28
forum: New to Ubuntu
---

### Post by likewise2 on 2019-04-28
Say I have to upgrade my Ubuntu from 17 to 18. Then, should I have to reinstall Ubuntu or I can put some command and it will be upgraded automatically. Sorry if its a too basic question to ask. I am a newbie to Linux.

---

### Post by cruzer001 on 2019-04-28
With a current release a upgrade can be done with a few clicks.
The 17 series (17.04 & 17.10) have reached end of life and harder to upgrade.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by deadflowr on 2019-04-28
In a normal situation (where the system is still supported and the new release is also still supported)  you have two options:

[URL="https://tutorials.ubuntu.com/tutorial/tutorial-upgrading-ubuntu-desktop#0"]The graphical desktop way
[/URL]
[The command line way]("https://help.ubuntu.com/lts/serverguide/installing-upgrading.html.en")


Note that both Ubuntu 17? releases are now dead so it's usually best to avoid upgrades from those.
It is possible to do such an upgrade see [EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")
But it's really far better in those situations to just do a clean install.

In all cases backups should be considered mandatory.

---

### Post by monkeybrain20122 on 2019-04-28
Even in cases where you can "upgrade" I still recommend backing up your data and do a clean install, a lot faster and problem free.

---

### Post by jdeca57 on 2019-04-28
in my experience there are two conditions in order to upgrade with minimal risks; the first is to keep your data safe and if you use cloud storage that is a big plus. Less safe is a separate /home partition but that is also a good solution. And secondly follow each upgrade, that means do not try to keep old versions but go from say 18.10 to 19.04. Coming from a 17.x is problematic. But an upgrade from 18.10 to 19.04? That works perfectly, probably because it is exhaustively tested.

---

### Post by likewise2 on 2019-04-29
Should I make a full backup of the system before upgrade?

---

### Post by Rubi1200 on 2019-04-29
Always best to do full backups before any major change to a system.

There is a list here of methods and tools for backups.
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by rbmorse on 2019-04-29
Always best to do full backups even if you don't plan on changing the system..<g>, but yes, especially before a system change. 

Having a full backup on hand is the best insurance against actually having to use it.

---

### Post by oldrocker99 on 2019-04-29
Many people over the years have had less than satisfactory results upgrading in place. **ALWAYS** back your data first, and create a separate /home partition, and a 64GB system folder using gparted, the install disk setup. Then, copy your backup to that partition, and new installs, if you mount that partition as /home, will require only an installation to the / partition, and that makes installations *easy!*

Here are instructions for making the partitions during an installation: [https://www.psychocats.net/ubuntu/installseparatehome](https://www.psychocats.net/ubuntu/installseparatehome).

Good luck!

---

