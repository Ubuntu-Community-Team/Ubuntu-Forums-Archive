---
title: "How to check what is requesting root"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Agester on 2013-03-10
Hey there everyone!  FYI if it matters, I'm using Ubuntu 12.04.  I was wondering is there a way to see either retroactively or in a log file what programs are requesting root?  Sometimes I may be randomly doing a task (i.e., browsing youtube, typing a paper on libreoffice etc.) Or just after logging in, a dialogue asking for me to approve a program root permissions pops up. While i know for the most part it may be something like ubuntu one trying to do an autoback up, but sometimes I'd like to be cautious and see what is asking before i approve.  Any assistance is much appreciated. Thanks for taking the time to read!  Edit: Awesome thanks for the quick response!

---

### Post by steeldriver on 2013-03-10
retroctively - you can look in /var/log/auth.log (because of log rotation you may need to go back to /var/log/auth.log.1, /var/log/auth.log.2.gz etc.)

---

