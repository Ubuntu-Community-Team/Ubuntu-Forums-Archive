---
title: "high iowait from time to time"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by todorakiggg on 2013-08-28
I am running ubuntu 13.04 and from time to time (very often) I see that iowait goes up to 30% and disk reading is something like 15-16 mb/s. I tried to close everything that was open (4-5 apps), but this did not solve the issues. I waited for some time and had to reboot???... Reboot, this is Linux on a first place??? :p
So how can I find out which application is causing the this high iowait? Besides this high numbers I can't seem to find anything disturbing, the system is working normally and so on.
Please advise?

---

### Post by sandyd on 2013-08-28
> **todorakiggg said:**
> I am running ubuntu 13.04 and from time to time (very often) I see that iowait goes up to 30% and disk reading is something like 15-16 mb/s. I tried to close everything that was open (4-5 apps), but this did not solve the issues. I waited for some time and had to reboot???... Reboot, this is Linux on a first place??? :p
So how can I find out which application is causing the this high iowait? Besides this high numbers I can't seem to find anything disturbing, the system is working normally and so on.
Please advise?

Try using iotop in a terminal to check what programs are using the I/O

**Install iotop**
```

sudo apt-get install iotop
```

**Use Iotop**
```
sudo iotop
```

---

### Post by tgalati4 on 2013-08-29
What are the SMART parameters of the hard disk?  Perhaps there is a hardware problem.  I had a desktop machine that was running Dapper Drake for years (literally, uptime for years) and one of the hard disk power connectors had vibrated loose.  The drive would randomly slow down, but not cause errors, just high IOWaits.  So I wrapped it with a little electrical tape to make a super tight fit to get a few more years out of it.

---

### Post by todorakiggg on 2013-08-29
iotop is a good suggestion, will give it a try.
Hardware issue, hmmm, I am using 5 months old configuration, so I doubt this to be the case, but if it happens more often I guess I'll have to call the seller.
Another question.
On this configuration I have one SSD where the OS is and another HDD where I store anything else. When I see the system showing high iowait, is it on the SSD drive or it is for the HDD, and how can I be sure, which drive is causing the issue?

---

### Post by tgalati4 on 2013-08-29
Check /var/log/syslog.  Look for SATA errors, they will be obvious.  Note the drive names (/dev/sda or /dev/sdb) and you should be able to narrow it down.  It's possible that your SSD has a problem and takes longer to write due to wear-leveling algorithms.

---

### Post by todorakiggg on 2013-08-30
Checked yesterday the syslogs, no SATA errors. I guess I'll have to check the logs when/if the problem occurs again.

---

