---
title: "Avoiding upgrade errors"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by lossanarch on 2013-03-07
Hi,

I recently upgraded my vps hosted server from 10.10 maverick to natty and then to oneiric and every step has been a colossal disaster. Apparently I'm stilll only up to 11.something and before I try to catch up more I'd really like to figure out why each step is such a hassle.

The first time I upgraded (maverick to natty) I used apt-get update and upgrade to get the latest packages, apt-get update-manager-core and then finally do-release-upgrade to begin. This then proceeded to upgrade and eventually failed complaining of:
```
[COLOR=#000000]*a copy of the C library was found in an unexpected directory:*[/COLOR]
[COLOR=#000000]*/lib/x86_64-linux-gnu/libc-2.13.so*[/COLOR]
[COLOR=#000000]*It is not safe to upgrade c library in this situation;*[/COLOR]
[COLOR=#000000]*please remove that copy of the C library or get it out of '/lib/x86_64-linux-gnu' and try again*[/COLOR]
```[COLOR=#000000]I didn't know how to fix it, so I restored and tried again. The second time worked without problems.
Then I updated from natty to oneiric and the same thing happened. Although I had backed up in between upgrades I wanted to avoid the lengthy restore and so, after hours of googling, I managed to fix libc then use apt-get -f install and/or possibly apt-get dist-upgrade (I don't remember which I ended up using, I remember seeing suggestions for both) to upgrade the rest.

Since then I've been chasing down strange errors like no mounted tmpfs, apache high memory usage, or broken localhost resolution.

Given that I've very-nearly-almost got it back to what I think is fully working, I'd really like to avoid all this happening again the next time.

Advice? Suggestions? Am I not performing the upgrade correctly?

Thanks in advance.[/COLOR]

---

### Post by tgalati4 on 2013-03-07
What prevented you from doing a clean install?  The time to back up data and install new may have been shorter than trying to perform step-wise upgrades.  As all linux distros mature, the frameworks that are used to build the operating system change.  Libraries change names and locations, configuration files change, and especially dependencies change on major packages.  All of these factors lead to breakage.

In-place upgrades are a neat feature of linux, and it is often done because it can be done, not because it is a good idea.  What is missing is--you guessed it--another framework.  Linux needs a framework to keep track of dependencies, config files, libraries, and other bits and pieces so that in-place upgrades are smoother.  The current apt package manager does 80% of the job, but the remaining 20% that is missing causes breakage.

---

### Post by lossanarch on 2013-03-07
Hmm, I guess I didn't even really consider doing a clean install.  I just assumed the in-place would nearly always work. Would you suggest sticking to LTS versions for servers then and just avoiding updating the release?

---

### Post by Bucky Ball on 2013-03-07
> **lossanarch said:**
> Would you suggest sticking to LTS versions for servers then and just avoiding updating the release?

A gigantic yes. For servers and production machines you want the LTS release. Don't bother with anything in between. You can upgrade from one LTS version to the next without the need to go stepwise through every other release. There is an LTS every two years but depending on your circumstances, using the same LTS for the five years of support is fine.

A clean install of 12.04 LTS would have taken MUCH less time than you needed to spend with this. Good luck. ;)

PS: Get your regular updates, fine, but don't UPGRADE to the next release. Remember:

sudo apt-get upgrade

... will NOT upgrade you to the next release but will upgrade any packages/software that needs upgrading. Only run that after you have done an update. Some people never bother with the above command on servers, just do the regular updates.

---

### Post by lossanarch on 2013-03-07
Thanks very much :)

---

