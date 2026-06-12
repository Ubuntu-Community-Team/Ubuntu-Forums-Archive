---
title: "Failed to download repository information"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by Junior UB on 2012-12-26
Every time I check for updates I get a message saying:

"Failed to download repository information"

Check your Internet connection.

Details:
W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I'm still new to Linux. What is this and how can I fix it?

---

### Post by Pjotr123 on 2012-12-26
Probably the PPA has ceased to exist. Handle PPA's with care:
[https://sites.google.com/site/easylinuxtipsproject/fatalmistakes](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

Better remove this one from your sources list.

---

### Post by Junior UB on 2012-12-26
I don't understand. Did I ruin my system? If so, can you please help me fix it?

---

### Post by plucky on 2012-12-26
> **Junior UB said:**
> I don't understand. Did I ruin my system? If so, can you please help me fix it?

No you didn't ruin your system.

The PPA that is giving the 404 error does not have a repository for **Precise** release.

See [Here](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/)

Just open your **Software Sources** and un-tick or delete that specific repository and then either reload your Source Indexes or run ```
sudo apt-get update
``` from a terminal to reload the Index files.


Good Luck

---

### Post by tak2100 on 2013-03-07
I had a similar problem.  Do you have an internet filter installed?  Something like OpenDNS filtering or Cybersitter can stop your PC from updating.  Whitelisting canonical.com seemed to work for me.  There might be other domains that need to be whitelisted as well.

---

