---
title: "Having trouble with installation"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-01-29
I'm in the live CD right now. When I attempt to install 11.10 32bit through my live dvd, I get to the screen where it asks you to make sure that you have at least 4gb drive space, and an internet connection. After hitting continue, it sits there for about 4 minutes loading, and then returns the error message:

"ubi-partman failed with exit code 141. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken."

I've tried quitting out and going back into the install procedure, but It's done this twice in a row now. Google-ing this issue wasn't much help for me either. Anyone know what's wrong?

---

### Post by oldfred on 2012-01-29
It seems related to some partitioning issue.

Did you look in  /var/log/syslog to see if it gave more information?

Some partitioning issues can be drive is or was in RAID, Windows has converted to dynamic partitions, chkdsk required on Windows, sometimes even BIOS settings that configure drives/partitions.

---

### Post by lechien73 on 2012-01-29
Hi, you may be better trying the install using the alternate CD ([http://releases.ubuntu.com/11.10/](http://releases.ubuntu.com/11.10/) and find the Alternate CD heading).

Some have reported that it's an issue with ubiquity, which the Alternate CD apparently doesn't use.

---

