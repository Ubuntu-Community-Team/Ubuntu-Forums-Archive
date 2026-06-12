---
title: "Hello just updated Ubuntu and got this message - do I have a problem?"
date: 2017-04-14
forum: New to Ubuntu
---

### Post by rjeev-kurian on 2017-04-14
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
W: The repository 'http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
rjeev@rjeev-VPCEG37FM:~$ 

This is what I got after updating using ( sudo apt-get update ) The part that bothers me is what comes after the "N:" which says "Data from such repository's can't be authenticated and there are potentially 
dangerous to use". Does this mean some one is attempting to send me a file or files that may act as a virus and or damage my computer? Sorry if this is too basic a question. I do not have much experience with Ubuntu but I do love using it. The computer I am using is an old Sony Vaio. I down loaded Ubuntu onto it and have been using it for quite a while. I'm running Ubuntu 16.04 LTS with 5.8 gigs of memory. The CPU is an Intel core i5-2450m cpu @ 2.50 ghz x 4. Intel Sandybridge Mobile. Disk space is 2.0 TB ( It did not initially come with this, but I removed the old disk and added this one. ) 

Thank you 
Yours Sincerely 
Rajeev Kurian

---

### Post by RobGoss on 2017-04-14
Hello and welcome, Try going to **Software & Updates**, click on **other software** Uncheck or delete the** PPA **you see listed below
```
E: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages 404 Not Found
```

Then try updating again, the** PPA **seems to be unsupported or no longer available

---

### Post by rjeev-kurian on 2017-04-14
Thank you RobGoss, I no longer seem to be getting that message. Have a great day. 
Rajeev Kurian

---

### Post by RobGoss on 2017-04-14
Your very welcome, is you have resolved your issue you can mark this thread as solved, please use the** Thread **tool at the top of this post

Have a great day

---

