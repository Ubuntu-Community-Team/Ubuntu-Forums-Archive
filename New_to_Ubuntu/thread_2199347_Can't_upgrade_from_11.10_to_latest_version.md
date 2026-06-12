---
title: "Can't upgrade from 11.10 to latest version"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by han4dguy on 2014-01-13
I sporadically use Ubuntu 11.10 and like it very much.  I am now reminded frequently that this version is no loger supported.  When i tried to upgrade I get the following message:
"An unresolvable problem occurred while calculating the upgrade:  
The package 'ubuntu-desktop-boulder' is marked for removal but it is in the removal blacklist.  

  This can be caused by:  
  * Upgrading to a pre-release version of Ubuntu  
  * Running the current pre-release version of Ubuntu  
  * Unofficial software packages not provided by Ubuntu  
 
 If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal."

I can't find the ubuntu-desktop-boulder package, or the removal blacklist. I am not running, or upgrading to, a pre-release version and so far as I know, the only software package not provided by Ubuntu is VMware Player.

How do I fix this so I can complete the upgrade (aside from wiping the disk and starting over)??

Thanx in advance, PGL

---

### Post by Frogs Hair on 2014-01-13
From 11.10 you would have upgrade in sequence from 11.10 - 13.10 one at a time. A backup of files if needed and clean installation of 13.10 would be a good idea. This would save a lot of time and avoid potential upgrade problems. Upgrades can take hours.

---

### Post by ian-weisser on 2014-01-13
Bug report you should subscribe to: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1068191](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1068191)
Unlikely to be fixed, 11.10 is -as you know- already past end-of-life. That's pretty much the definition of "unsupported".

Have you tried to remove the ubuntu-desktop-boulder package? How? What happened?

---

### Post by TheFu on 2014-01-13
I'd need to see the exact error messages to be of any help.
Run these commands from a terminal, capture any errors and post them back here wrapped in "code" tags (Adv Reply):
1) sudo apt-get update
2) sudo apt-get dist-upgrade
3) sudo do-release-upgrade

If there is any error with step 1, DO NOT CONTINUE.
If there is any error with step 2, DO NOT CONTINUE.

If there aren't any errors, this should take you to 12.04-LTS, which is supported until 2017. That is the release you want until ready to migrate to 14.04 in June at the earliest.  People like you and I should stay on LTS releases.

---

### Post by TheFu on 2014-01-13
> **Frogs Hair said:**
> From 11.10 you would have upgrade in sequence from 11.10 - 13.10 one at a time. A a backup of files if needed and clean installation of 13.10 would be a good idea. This would save a lot of time and avoid potential upgrade problems. Upgrades can take hours.

**Update - my mistake. I apologize.  **

Most people, including the OP, need to be on LTS releases, not the 6-9 month support releases for developers. The OP has displayed that he doesn't stay current with Ubuntu releases and clearly needs LTS.  11,10 --> 12.04 and should stop there until the next LTS release is out and has a month or so of stability.  Then, when ready, 12.04 --> 14.04 - LTS to LTS.

I believe we should try to avoid creating more work than necessary for people who don't need the latest release, but just want to use the OS.

---

### Post by ppjdee on 2014-01-13
Im not much help, but i do recommend downloading 12.04 lts and doing a fresh install.. Like other person stated, it can avoid a lot of headaches and would be quicker.

---

### Post by Bucky Ball on 2014-01-13
> **TheFu said:**
> Most people, including the OP, need to be on LTS releases, not the 6-9 month support releases for developers. The OP has displayed that he doesn't stay current with Ubuntu releases and clearly needs LTS.  11,10 --> 12.04 and should stop there until the next LTS release is out and has a month or so of stability.  Then, when ready, 12.04 --> 14.04 - LTS to LTS.

I believe we should try to avoid creating more work than necessary for people who don't need the latest release, but just want to use the OS.

+1. 11.10>12.04 LTS>14.04 LTS>16.04 LTS ad infinitum ... ;)

---

### Post by Frogs Hair on 2014-01-13
> **Bucky Ball said:**
> +1. 11.10>12.04 LTS>14.04 LTS>16.04 LTS ad infinitum ... ;)


This is the most practical approach if the latest release is not  a requirement. A clean installation of 12.04 is even better !

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

