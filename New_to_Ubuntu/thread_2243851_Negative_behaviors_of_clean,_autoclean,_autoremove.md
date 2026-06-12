---
title: "Negative behaviors of clean, autoclean, autoremove?"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-11
I just started learning Linux and I am compiling a list of commands and its functions that optimize the system. I came across commands such as clean, autoclean, and autoremove. I have read that some of these commands may cause unintended consequences. From what I've read, however, I don't see how these commands are not safe in the sense that I can run them any time and expect them to optimize the system. 

apt-get clean flushes the cache of packages that are to be installed, right? So isn't the worst scenario that can happen is that I have to download the package again?
apt-get autoclean does the same thing as apt-get clean except it does not remove the cache of the latest version, so it's even "safer" than the worst case scenario of apt-get clean, right?

As for apt-get autoremove, it "removes orphaned packages that were installed as dependencies, *but are no longer*."&#8203; They may not be dependencies for the orphaned package, but what if they are dependencies for a package that I am using--will it delete it? If not, How could this command be "dangerous" or produce unintended consequences?

Thanks.

P.S. What other safe commands that optimize Linux should I be aware of? Anything from updating drivers to clearing cache of certain programs. I am not afraid to get dirty as long as there are clear instructions and I understand what I'm doing and the risks.

---

### Post by deadflowr on 2014-09-11
Duplicate thread
here
[http://ubuntuforums.org/showthread.php?t=2243852](http://ubuntuforums.org/showthread.php?t=2243852)

This one is closed

---

