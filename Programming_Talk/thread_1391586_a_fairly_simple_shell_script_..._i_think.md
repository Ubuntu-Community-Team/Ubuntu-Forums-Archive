---
title: "a fairly simple shell script ... i think"
date: 2010-01-27
forum: Programming Talk
---

### Post by crownedzero on 2010-01-27
my bash/shell scripting is minimal so I'm hoping to get a small bit of help from the community. I've recently started tethering my android phone and was hoping to set this up to a script i could throw on my desktop.

the process can be found at [http://code.google.com/p/proxoid/wiki/installationLinux](http://code.google.com/p/proxoid/wiki/installationLinux) now the only part i need is the "./adb forward tcp:8080 tcp:8080". also if possible i'd like to have it reconfigure the browser without having to open it up each time and do it manually. if at all possible have another script to kill the process and revert the browser settings. think you guys/girls can be of any assistance? thanks,

---

### Post by chewearn on 2010-01-27
See here on how to affect the system wide proxy settings from a script:
[http://ubuntuforums.org/showthread.php?t=1390260](http://ubuntuforums.org/showthread.php?t=1390260)

Then, set Firefox to use "System Proxy Settings".

---

